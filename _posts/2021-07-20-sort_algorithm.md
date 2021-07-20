---
layout: post
title:  "정렬 알고리즘"
---

# 정렬 알고리즘

## 선택 정렬(selection sort)

```java
import java.util.Arrays;
/** 처리되지 않은 원소 중에서 가장 작은 원소를 선택해 맨 앞으로 보내는 것을 반복 **/
public class Selection_Sort {
    public static void main(String[] args) {
        int[] array = {7, 5, 9, 0, 3, 1, 6, 2, 4, 8};

        // step 1. index 0부터 9까지의 원소 비교 후 가작 작은 원소의 index가 min_index
        // step 2. index 1부터 9까지의 원소 비교 후 가작 작은 원소의 index가 min_index
        // .. 이하 반복
        for (int i = 0; i < array.length; i++) {
            int min_index = i; // 가장 작은 원소의 인덱스
            for (int j = i+1; j < array.length; j++) {
                if (array[min_index] > array[j]) {
                    min_index = j;
                }
            }
            // 비교 후 min_index에 있는 원소를 맨 앞(index i)으로 보냄
            swap(i, min_index, array[i], array[min_index], array);
            // System.out.println(Arrays.toString(array));
        }
        System.out.println(Arrays.toString(array));
    }

    public static int[] swap(int i, int min_index, int a, int b, int[] array) {
        array[i] = b;
        array[min_index] = a;
        return array;
    }


}

```

