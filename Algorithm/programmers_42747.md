
## [42747. H-Index](https://programmers.co.kr/learn/courses/30/lessons/42747)

**Problem :**

H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과1에 따르면, H-Index는 다음과 같이 구합니다.

어떤 과학자가 발표한 논문 n편 중, h번 이상 인용된 논문이 h편 이상이고 나머지 논문이 h번 이하 인용되었다면 h의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.

- 과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.
- 논문별 인용 횟수는 0회 이상 10,000회 이하입니다.


**Source Code :**

```java
import java.util.Arrays;

class programmers_42747 {
    public int solution(int[] citations) {
        int answer = 0;
        int length = citations.length;

        Arrays.sort(citations);

        for (int i = 0; i < length; i++) {
            int k =  length - i; 
            if (k <= citations[i]) {
                answer = k;
                break;
            }
        }
        return answer;
    }
}
```

**Test Code 1:**
```java
public class programmers_42747Test {
    programmers_42747 s = new programmers_42747();

    @Test
    public void test(){
        Assert.assertEquals(s.solution(new int[]{3, 0, 6, 1, 5}),3);
        Assert.assertEquals(s.solution(new int[]{5, 5, 5, 5}),4);
    }
}
```

**Experience 1:**

k보다 많이 인용된 논문이 k개일때를 세면 된다. 이 문제는 문제 이해하는것만 시간이 좀 걸릴뿐, 쉬운 문제인 것 같다. 