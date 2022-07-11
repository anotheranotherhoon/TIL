```js
const mergeTwoLists = function (list1, list2) {
  const arr = [];
  while (list1.length !== 0 && list2.length !== 0) {
    if (list1[0] < list2[0]) {
      arr.push(list1.shift());
    } else {
      arr.push(list2.shift());
    }
  }
  if (list1.length === 0) {
    arr.push(...list2);
  } else {
    arr.push(...list1);
  }

  return arr;
};

```