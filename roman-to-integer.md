# 풀이
```ts
function romanToInt(s: string): number {
    let ans = 0;

    const dict = {
        "I": 1,
        "V": 5,
        "X": 10,
        "L": 50,
        "C": 100,
        "D": 500,
        "M": 1000
    }

    for (let i = 0; i < s.length; i++) {
        if (dict[s[i]] < dict[s[i + 1]]) {
            ans += dict[s[i + 1]] - dict[s[i]]
            i++;
        }
        else {
            ans += dict[s[i]]
        }
    }

    return ans;
};
```

# GPT 버전
```ts
function romanToInt(s: string): number {
    // 1. 로마 숫자 -> 정수 매핑
    const map: Record<string, number> = {
        I: 1,
        V: 5,
        X: 10,
        L: 50,
        C: 100,
        D: 500,
        M: 1000,
    };

    let total = 0;

    // 2. 문자열 순회
    for (let i = 0; i < s.length; i++) {
        const curr = map[s[i]];
        const next = map[s[i + 1]]; // 다음 값 (없으면 undefined)

        // 3. 현재 값이 다음 값보다 작으면 빼기, 아니면 더하기
        if (next !== undefined && curr < next) {
            total -= curr;
        } else {
            total += curr;
        }
    }

    return total;
}
```
타입에 대해 더 엄밀히 표현하는거 같다.