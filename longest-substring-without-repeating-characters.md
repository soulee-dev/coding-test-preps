# 해결
```ts
function lengthOfLongestSubstring(s: string): number {
    let ans = 0;

    for (let i = 0; i < s.length; i++) {
        const seen = new Set<string>();
        
        for (let j = i; j < s.length; j++) {
            const ch = s[j];

            if (seen.has(ch)) {
                break;
            }

            seen.add(ch);
            ans = Math.max(ans, j - i + 1);
        }
    }

    return ans;
};
```

하지만 더 효율적인 방법이 있을거 같다.

```ts
function lengthOfLongestSubstring(s: string): number {
    let l = 0;
    let maxLen = 0;
    const last = new Map<string, number>();

    for (let r = 0; r < s.length; r++) {
        const ch = s[r];

        if (last.has(ch) && (last.get(ch) as number) >= l) {
            l = (last.get(ch) as number) + 1;
        }

        last.set(ch, r);

        const currLen = r - l + 1;
        if (currLen > maxLen) maxLen = currLen;
    }

    return maxLen;
};
```
Sliding Window 방식. O(n)