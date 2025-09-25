# 나의 풀이
```ts
function twoSum(nums: number[], target: number): number[] {
    for (let i = 0; i < nums.length -1; i++) {
        for (let j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] == target) return [i, j]
        }
    }

    return []
};
```

Brute-force 방식 O(n²)

# 다른 풀이
```ts
function twoSum(nums: number[], target: number): number[] {
    const idxByValue = new Map<number, number>();

    for (let i = 0; i < nums.length; i++) {
        const cur = nums[i];
        const need = target - cur;

        if (idxByValue.has(need)) {
            return [idxByValue.get(need)!, i];
        }

        idxByValue.set(cur, i);
    }

    throw new Error("No solution exists");
};
```

# 자료구조
## `{}` vs `Map` 차이 요약

* **키 타입**

  * `{}`: 문자열/심볼만 가능 (숫자도 내부적으로 문자열 변환됨)
  * `Map`: 모든 타입 가능 (숫자, 객체, 배열 등)

* **순서**

  * `{}`: 기본적으로 순서 보장 X (일부 규칙 있음)
  * `Map`: 삽입 순서 100% 보장

* **성능**

  * `{}`: 단순/작은 데이터에 적합
  * `Map`: 대량 데이터/빠른 탐색에 최적화

* **사용성**

  * `{}`: 문법 단순 (`obj[key]`)
  * `Map`: 메서드 풍부 (`.set`, `.get`, `.has`, `.delete`)
