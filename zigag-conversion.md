# 풀이
```sh
function convert(s: string, numRows: number): string {
    if (numRows === 1 || numRows >= s.length) return s;

    const rows: string[] = Array.from({ length: numRows }, () => "");

    let r = 0;
    let dir = 1;

    for (const ch of s) {
        rows[r] += ch;

        r += dir;

        if (r === 0 || r === numRows - 1) dir *= -1;
    }

    return rows.join("");
};
```