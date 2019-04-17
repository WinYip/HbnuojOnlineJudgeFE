<template>
  <div>
    <Panel>
      <div slot="title">{{$t('m.Problems_List')}}</div>
      <Table v-if="contestRuleType == 'ACM' || OIContestRealTimePermission"
             :columns="ACMTableColumns"
             :data="problems"
             @on-row-click="goContestProblem"
             no-data-text="No Problems"></Table>
      <Table v-else
             :data="problems"
             :columns="OITableColumns"
             @on-row-click="goContestProblem"
             no-data-text="No Problems"></Table>
    </Panel>
  </div>
</template>

<script>
  import {mapState, mapGetters} from 'vuex'
  import {ProblemMixin} from '@oj/components/mixins'

  export default {
    name: 'ContestProblemList',
    mixins: [ProblemMixin],
    data () {
      return {
        ACMTableColumns: [
          {
            title: 'ID',
            key: '_id',
            sortable: true,
            width: 150,
            sortType: 'asc',
            sortMethod: (a, b, type) => {
              let aa = parseInt(a)
              let bb = parseInt(b)
              if (type === 'desc') {
                return aa < bb
              } else {
                return aa > bb
              }
            }
          },
          {
            title: '题目',
            key: 'title'
          },
          {
            title: '提交次数',
            key: 'submission_number'
          },
          {
            title: 'AC率',
            render: (h, params) => {
              return h('span', this.getACRate(params.row.accepted_number, params.row.submission_number))
            }
          }
        ],
        OITableColumns: [
          {
            title: 'ID',
            key: '_id',
            width: 150
          },
          {
            title: '题目',
            key: 'title'
          }
        ]
      }
    },
    mounted () {
      this.getContestProblems()
    },
    methods: {
      getContestProblems () {
        this.$store.dispatch('getContestProblems').then(res => {
          if (this.isAuthenticated) {
            if (this.contestRuleType === 'ACM') {
              this.addStatusColumn(this.ACMTableColumns, res.data.data)
            } else if (this.OIContestRealTimePermission) {
              this.addStatusColumn(this.ACMTableColumns, res.data.data)
            }
          }
        })
      },
      goContestProblem (row) {
        this.$router.push({
          name: 'contest-problem-details',
          params: {
            contestID: this.$route.params.contestID,
            problemID: row._id
          }
        })
      }
    },
    computed: {
      ...mapState({
        problems: state => state.contest.contestProblems
      }),
      ...mapGetters(['isAuthenticated', 'contestRuleType', 'OIContestRealTimePermission'])
    }
  }
</script>

<style scoped lang="less">
</style>
