<p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 10px; color: rgb(51, 51, 51); font-family: &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 14px; white-space: normal;">
    你和你的朋友，两个人一起玩&nbsp;<a href="http://undefined" target="_blank" style="box-sizing: border-box; background-color: transparent; color: rgb(0, 136, 204); text-decoration-line: none;">Nim游戏</a>：桌子上有一堆石头，每次你们轮流拿掉&nbsp;1 - 3 块石头。 拿掉最后一块石头的人就是获胜者。你作为先手。
</p>
<p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 10px; color: rgb(51, 51, 51); font-family: &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 14px; white-space: normal;">
    你们是聪明人，每一步都是最优解。 编写一个函数，来判断你是否可以在给定石头数量的情况下赢得游戏。
</p>
<p style="box-sizing: border-box; margin-top: 0px; margin-bottom: 10px; color: rgb(51, 51, 51); font-family: &quot;Helvetica Neue&quot;, Helvetica, Arial, sans-serif; font-size: 14px; white-space: normal;">
    <span style="box-sizing: border-box; font-weight: 700;">示例:</span>
</p>
<pre style="box-sizing: border-box; overflow: auto; font-family: Menlo, Monaco, Consolas, &quot;Courier New&quot;, monospace; font-size: 13px; padding: 9.5px; margin-top: 0px; margin-bottom: 10px; line-height: 1.42857; color: rgb(51, 51, 51); word-break: break-all; word-wrap: break-word; background-color: rgb(245, 245, 245); border: 1px solid rgb(204, 204, 204); border-radius: 4px;">输入: 4输出: false 
解释: 如果堆中有 4 块石头，那么你永远不会赢得比赛；
     因为无论你拿走 1 块、2 块 还是 3 块石头，最后一块石头总是会被你的朋友拿走。</pre>
<p>
    <br/>
</p>

``` java
class Solution {
    public boolean canWinNim(int n) {
        return n%4!=0;
    }
}
```