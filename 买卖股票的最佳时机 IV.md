给定一个数组，它的第 i 个元素是一支给定的股票在第 i 天的价格。<br>

设计一个算法来计算你所能获取的最大利润。你最多可以完成 k 笔交易。<br>

注意: 你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。<br>

示例 1:<br>

输入: [2,4,1], k = 2<br>
输出: 2<br>
解释: 在第 1 天 (股票价格 = 2) 的时候买入，在第 2 天 (股票价格 = 4) 的时候卖出，这笔交易所能获得利润 = 4-2 = 2 。<br>
示例 2:<br>

输入: [3,2,6,5,0,3], k = 2<br>
输出: 7<br>
解释: 在第 2 天 (股票价格 = 2) 的时候买入，在第 3 天 (股票价格 = 6) 的时候卖出, 这笔交易所能获得利润 = 6-2 = 4 。<br>
     随后，在第 5 天 (股票价格 = 0) 的时候买入，在第 6 天 (股票价格 = 3) 的时候卖出, 这笔交易所能获得利润 = 3-0 = 3 。<br><br>


``` java
class Solution {
    public int maxProfit(int k, int[] prices) {
        if(k < 1){
            return 0;
        }
        if(prices.length < 2){
            return 0;
        }
        int len = prices.length;
        if(k*2 >= len-1){//买卖次数足够多
            return maxProfit0(prices);
        }
        if(k == 2){
            return maxProfit2(prices);
        }
        int mustSell[][] = new int [len][k+1];
        int globalSell[][] = new int [len][k+1];

        for(int j=1;j<=k;j++){
            for(int i=1;i<len;i++){//交易k次
                int profit = prices[i] - prices[i-1];
                profit = profit >= 0 ? profit : 0;
                mustSell[i][j] = Math.max(globalSell[i-1][j-1] + profit,mustSell[i-1][j] + prices[i] - prices[i-1]);
                globalSell[i][j] = Math.max(globalSell[i-1][j],mustSell[i][j]);
            }
        }

        return globalSell[prices.length-1][k];
    }
    public int maxProfitk(int dp[][],int k,int start,int count) {
        if(k == 0 || start >= dp.length - 1){
            return count;
        }
        int result = 0;
        for(int i=start;i<dp.length;i++){
            for(int j=i+1;j<dp.length;j++){
                if(dp[i][j] > 0){
                    int temp = maxProfitk(dp,k-1,j+1,dp[i][j] + count);
                    result = temp > result ? temp : result;
                }
            }
        }
        return result;
     }
    public int maxProfit0(int[] prices) {
        if(prices.length < 2){
            return 0;
        }
        int len = prices.length;
        int result = 0;
        for(int i=1;i<len;i++){
            if(prices[i] > prices[i-1]){
                result += prices[i] - prices[i-1];
            }
        }

        return result;
     }

    public int maxProfit2(int[] prices) {
         int len = prices.length;
         if(len<=1)return 0;
         int max=0;

         int dp1[] = new int[len];
           int curmin= prices[0];
           for(int i=1;i<len;i++){
               max = max < prices[i] - curmin ? prices[i] - curmin : max;
               curmin =  prices[i] < curmin ?  prices[i] : curmin;
               dp1[i] = max;
           }

           int curmax= prices[len-1];
           max=0;
           int dp2[] = new int[len];
           for(int i=len-1;i>=0;i--){
               max = max < curmax-prices[i] ? curmax-prices[i]  : max;
               curmax =  prices[i] > curmax ?  prices[i] : curmax;
               dp2[i] = max;
           }
           max=0;
           for(int i=len-1;i>0;i--){
               max = max < dp1[i]+dp2[i] ? dp1[i]+dp2[i]  : max;

           }
    return max;

    }
}
```