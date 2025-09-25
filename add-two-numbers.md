# 정답
```ts
function addTwoNumbers(l1: ListNode | null, l2: ListNode | null): ListNode | null {
    let carry: number = 0;
    let dummy = new ListNode(0);
    let curr = dummy;

    while (l1 || l2 || carry) {
        let sum = (l1?.val ?? 0) + (l2?.val ?? 0) + carry
        carry = sum >= 10 ? 1 : 0

        curr.next = new ListNode(sum % 10)

        curr = curr.next
        l1 = l1?.next
        l2 = l2?.next
    }

    return dummy.next;
};
```

이번 문제는 기본적인 Linked List 응용 문제였다.
핵심 아이디어 자체는 바로 떠올릴 수 있었지만, 오랜만에 Linked List를 다루다 보니 세부 구현에서 잠시 막히는 부분이 있었다.

구현 과정에서는 더미 노드(dummy node)를 활용해 코드 흐름을 단순화했고, carry(올림 수) 처리를 통해 각 자리수를 계산했다.
또한 TypeScript 문법을 적극적으로 사용하여 가독성과 안정성을 높였다.

결과적으로, 직관적인 아이디어를 간단하고 깔끔하게 코드로 옮길 수 있었다.