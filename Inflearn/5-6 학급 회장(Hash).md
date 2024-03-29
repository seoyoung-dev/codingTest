## 문제 설명

학급 회장을 뽑는데 후보로 기호 A, B, C, D, E 후보가 등록을 했습니다.
투표용지에는 반 학생들이 자기가 선택한 후보의 기호(알파벳)가 쓰여져 있으며 선생님은 그 기호를 발표하고 있습니다. <br />
선생님의 발표가 끝난 후 어떤 기호의 후보가 학급 회장이 되었는지 출력하는 프로그램을 작 성하세요. 반드시 한 명의 학급회장이 선출되도록 투표결과가 나왔다고 가정합니다.

<br />
<br />

## 입력/출력 예제

| 입력            | 출력 |
| --------------- | ---- |
| BACBACCACCBDEDE | C    |

<br />
<br />

## 내 답안

```js
function solution(s) {
    let answer;
    let splitted = s.split("");
    let dict = {};
    splitted.forEach((ele) => {
        if (dict[ele] === undefined) dict[ele] = 0;
        dict[ele] += 1;
    });
    for (let candidate in dict) {
        if (answer === undefined) answer = candidate;
        if (dict[candidate] > dict[answer]) answer = candidate;
    }
    return answer;
}

let str = "BACBACCACCBDEDE";
console.log(solution(str));
```

-   알고리즘을 사용하지 않은 단순 구현 방법

</br>  
</br>

## 모범답안

```js
function solution(s) {
    let answer;
    let sH = new Map();
    for (let x of s) {
        if (sH.has(x)) sH.set(x, sH.get(x) + 1);
        else sH.set(x, 1);
    }
    let max = Number.MIN_SAFE_INTEGER;
    for (let [key, val] of sH) {
        if (val > max) {
            max = val;
            answer = key;
        }
    }
    return answer;
}

let str = "BACBACCACCBDEDE";
console.log(solution(str));
```

-   sH : string Hash
