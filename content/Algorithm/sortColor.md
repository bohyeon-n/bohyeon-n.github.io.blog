# sort colors

Given an array with n objects colored red, white or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

# 나의 풀이

- in-place 알고리즘이란 원소들의 개에 비해서 충분히 무시할 만한 저장 공간만을 더 사용하여 정렬 알고리즘들을 의미한다.

- 버블 정렬
  - 두 인접한 원소를 검사하여 큰 수를 뒤로 보내는 간단한 알고리즘
  - 다른 정렬 알고리즘에 비해 속도가 상당히 느리다.

```js
var sortColors = function(nums) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < nums.length - i; j++) {
      if (nums[j] > nums[j + 1]) {
        let temp = nums[j];
        nums[j] = nums[j + 1];
        nums[j + 1] = temp;
      }
    }
  }
};
```

# 다른 사람 풀이

- 원소의 종류가 3 가지이다. 0,1,2 라는 점을 이용한다.
- 반복문을 돌면서 원소가 0 이라면, 첫 번 째 원소에 고정시킨다. 그리고 다음 0 을 찾아서 그 다음 원소로 정한다.
- 2 라면, 맨 끝 원소로 고정시키고 맨 끝보다 index 가 작은 원소를 찾아서 다시 고정시킨다.
- 이 작업을 계속해서 반복한다.
- 그럼 0 과 2 가 맨 앞과 끝으로 정렬된다.
- 1 은 자동적으로 그 중간에 위치하게 된다.

```js
var sortColors = function(nums) {
  var low = 0,
    high = nums.length - 1,
    temp;

  for (var i = 0; i <= high; ) {
    if (nums[i] === 0) {
      temp = nums[i];
      nums[i] = nums[low];
      nums[low] = temp;
      i++;
      low++;
    } else if (nums[i] == 2) {
      temp = nums[i];
      nums[i] = nums[high];
      nums[high] = temp;
      high--;
    } else {
      i++;
    }
  }
};
```
