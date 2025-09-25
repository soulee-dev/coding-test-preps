# 풀이
```ts
function isPalindrome(x: number): boolean {
    const str = x.toString();
    const reversedStr = str.split("").reverse().join("")

    return str == reversedStr;
};
```

문자열로 접근했는데, 숫자로도 접근 가능하겠다.

# 다른 풀이
```ts
function isPalindrome(x: number): boolean {
    if (x < 0 || (x % 10 === 0 && x !== 0)) return false;

    let reversedHalf = 0;

    while (x > reversedHalf) {
        const digit = x % 10;

        reversedHalf = reversedHalf * 10 + digit;
        x = Math.floor(x / 10);
    }

    return x === reversedHalf || x === Math.floor(reversedHalf / 10);
};
```