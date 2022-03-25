# [프로그래머스] K번째수
```java
package CodingTest;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class K번째수 {
    public static void main(String[] args) {
        int[] array = {1, 5, 2, 6, 3, 7, 4};
        int[][] commands = {{2, 5, 3},
                            {4, 4, 1},
                            {1, 7, 3}};

        Solution solution = new Solution();
        int[] result =  solution.solution(array, commands);
        System.out.println("result = " + Arrays.toString(result));

    }

    static class Solution {
        public int[] solution(int[] array, int[][] commands) {
            //int[] answer = {};
            List<Integer> result = new ArrayList<>();
            //List<Integer> temp = Arrays.stream(array).boxed().collect(Collectors.toList());
            List<Integer> temp = new ArrayList<>();
            int a, b, c, d;
            for (int i = 0; i < commands.length; i++) {
                a = commands[i][0];
                b = commands[i][1];
                c = commands[i][2];
                for (int j = a - 1; j < b; j++) {
                    temp.add(array[j]);
                }
                Collections.sort(temp);
                d = temp.get(c - 1);
                result.add(d);
                temp.clear();
            }

            return result.stream().mapToInt(i -> i).toArray();
        }
    }
}

```


