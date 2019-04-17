<template>
  <panel>
    <div slot="title">{{$t('m.Frequently_Asked_Questions')}}</div>
    <div class="content markdown-body">
      <ul>
        <li>输入和输出在哪里？
          <p>您的程序应从 <code>stdin</code>('标准输入') 读取输入并将输出写入 <code>stdout</code>('标准输出')。
            例如，您可以在C中使用 <code>scanf</code> 或在C++中使用 <code>cin</code> 从 stdin 中读取输入,和在C中使用 <code>printf</code> 或在C++中使用 <code>cout</code> 将输入写入 stdout 中。
            用户程序不允许读取或写入文件, 否则你将得到一个 <code>Runtime Error</code> 的错误。
          </p>
        </li>
        <li>程序提交后的执行时间的含义是什么？
        <p>OnlineJudge可能会使用不同的输入文件多次测试您的代码。
          如果您的代码在每个输入文件的时间限制内给出正确答案，则显示的执行时间是每个测试用例花费的最大时间。否则，执行时间就没有意义了。
        </p>
        </li>
        <li>我如何使用C++ Int64？
          <p>你应该声明为 <code>long long</code> 并且使用 <code>cin/cout</code> 或者 <code>%lld</code> 输出, 使用 <code> __int64</code> 的结果将会是获得一个 <code>Compile Error</code> 错误 。</p>
        </li>
        <li>Java规范？
          <p>所有程序必须以 <code>Main</code> 类中的静态main方法开头. 要使用公共类: 甚至 <code>Main</code>必须是非公共类以避免编译错误。使用缓冲 I/O 以避免由于过度刷新而超出时间限制。</p>
        </li>
        <li>关于格式错误？
          <p>在这个oj中没有任何格式错误。评测机将会修正你输出的 <b>最后</b> 一行空行。
            如果它与正确的输出仍然不同，结果将是 <code>Wrong Answer</code> 错误.</p>
        </li>
        <li>如何反馈有关此oj的错误？
          <p>你可以向oj管理员反馈系统出现的问题，如遇到题目有错误的可以发送题目信息到邮箱776853031@qq.com或者2495515238@qq.com。
          </p>
        </li>
      </ul>
    </div>
  </panel>
</template>

<script>
</script>

<style lang="less" scoped>
  .content {
    font-size: 16px;
    margin: 0 50px 40px 50px;
    > ul {
      list-style: disc;
      li {
        font-size: 16px;
        margin-top: 20px;
        &:first-child {
          margin-top: 0;
        }
        p {
          font-size: 14px;
          margin-top: 5px;
        }
      }
    }
  }
</style>
