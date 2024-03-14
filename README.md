<details>
<summary>1. 买卖股票的最佳时机</summary>

> 给定一个数组 prices ，它的第 i 个元素 prices[i] 表示一支给定股票第 i 天的价格。  
> 你只能选择 某一天 买入这只股票，并选择在 未来的某一个不同的日子 卖出该股票。设计一个算法来计算你所能获取的最大利润。  
> 返回你可以从这笔交易中获取的最大利润。如果你不能获取任何利润，返回 0 。

```ts
/**
 * 从左侧遍历，保存每次的最大利润，计算每次的左侧最小值
*/
function maxProfit(prices: number[]): number {
    let profit = 0; // 当前最大利润
    let minPrice = prices[0]; // 左侧最小值
    for (const p of prices) {
        profit = Math.max(profit, p - minPrice); // 当前最大利润
        minPrice = Math.min(minPrice, p); // 当前左侧最小值
    }

    return profit;
};
```
</details>

---

<details>
<summary>2. 验证回文串</summary>

> 如果在将所有大写字符转换为小写字符、并移除所有非字母数字字符之后，短语正着读和反着读都一样。则可以认为该短语是一个 回文串 。    
> 字母和数字都属于字母数字字符。    
> 给你一个字符串 s，如果它是 回文串 ，返回 true ；否则，返回 false 。

```ts
/**
 * 遍历字符串，首尾对比，奇数的话，中间那个不用比较
*/
function isPalindrome(s: string): boolean {
    // 转成小写，去除异常字符
    const str = s.toLowerCase().replace(/[\W_]/ig, '');
    // 获取字符串长度
    const l = str.length;
    for (let i = 0; i < Math.floor(l / 2); i++) {
        if(str[i] !== str[l - i - 1]) {
            return false;
        }
    }
    return true;
};
```
</details>

---

<details>
<summary>3. 赎金信</summary>

> 给你两个字符串：ransomNote 和 magazine ，判断 ransomNote 能不能由 magazine 里面的字符构成。    
> 如果可以，返回 true ；否则返回 false 。    
> magazine 中的每个字符只能在 ransomNote 中使用一次。    

```ts
/**
 * 先保存出现的字母，再消费，如果不够则失败
*/
function canConstruct(ransomNote: string, magazine: string): boolean {
    // 26 个字母
    const cnt = Array(26).fill(0)
    for (const c of magazine) {
        // 每个字母出现的次数
        ++cnt[c.charCodeAt(0) - 97];
    }

    for (const c of ransomNote) {
        // 出现的字母不够用，则失败
        if (--cnt[c.charCodeAt(0) - 97] < 0) {
            return false;
        }
    }
    return true;
};
```
</details>

