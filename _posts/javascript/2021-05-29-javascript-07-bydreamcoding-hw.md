---
title: "Dream Coding-JavaScript 08강 숙제 Array interface"
date: 2021-05-29
category: javascript
tags:
  - DreamCoding
toc: true
toc_sticky: true
toc_label: “8. 배열 제대로 알고 쓰자. 자바스크립트 배열 개념과 APIs 총정리”
---



Array APIs Interface

## interface Array<T>

#### length: number
* Gets or sets the length of the array. This is a number one higher than the highest index in the array.  
* 배열의 길이를 가져 오거나 설정합니다. 이것은 배열에서 가장 높은 인덱스보다 1 높은 숫자입니다.  

#### toString(): string;
* Returns a string representation of an array.  
* 배열의 문자열 표현을 반환합니다.

#### toLocaleString(): string;
* Returns a string representation of an array. The elements are converted to string using their toLocalString methods.
* 배열의 문자열 표현을 반환합니다. 요소는 toLocalString 메소드를 사용하여 문자열로 변환됩니다.

#### pop(): T | undefined;
* Removes the last element from an array and returns it.
* If the array is empty, undefined is returned and the array is not modified.
* 배열에서 마지막 요소를 제거하고 반환합니다.
* 배열이 비어 있으면 undefined가 반환되고 배열이 수정되지 않습니다. 

#### push(...items: T[]): number;
* Appends new elements to the end of an array, and returns the new length of the array.
* `items` New elements to add to the array.
* 배열 끝에 새 요소를 추가하고 배열의 새 길이를 반환합니다.
* `items` 배열에 추가 할 새 요소.

#### concat(...items: ConcatArray<T>[]): T[];
* Combines two or more arrays.
* This method returns a new array without modifying any existing arrays.
* `items` Additional arrays and/or items to add to the end of the array.
* 두 개 이상의 배열을 결합합니다.
* 이 메서드는 기존 배열을 수정하지 않고 새 배열을 반환합니다.
* `items` 배열 끝에 추가 할 추가 배열 및 / 또는 항목입니다.

#### concat(...items: (T | ConcatArray<T>)[]): T[];
* Combines two or more arrays.
* This method returns a new array without modifying any existing arrays.
* `items` Additional arrays and/or items to add to the end of the array.

#### join(separator?: string): string;
* Adds all the elements of an array into a string, separated by the specified separator string.
* `separator` A string used to separate one element of the array from the next in the resulting string. If omitted, the array elements are separated with a comma.
* 배열의 모든 요소를 지정된 구분자 문자열로 구분하여 문자열에 추가합니다.
* `separator` 배열의 한 요소를 결과 문자열에서 다음 요소와 구분하는 데 사용되는 문자열. 생략하면 배열 요소가 쉼표로 구분됩니다.

#### reverse(): T[];
* Reverses the elements in an array in place.
* This method mutates the array and returns a reference to the same array.
* 배열의 요소를 제자리에서 반전합니다.
* 이 메서드는 배열을 변경하고 동일한 배열에 대한 참조를 반환합니다.

#### shift(): T | undefined;
* Removes the first element from an array and returns it.
* If the array is empty, undefined is returned and the array is not modified.
* 배열에서 첫 번째 요소를 제거하고 반환합니다.
* 배열이 비어 있으면 undefined가 반환되고 배열이 수정되지 않습니다. 

#### slice(start?: number, end?: number): T[];
* Returns a copy of a section of an array.
* For both start and end, a negative index can be used to indicate an offset from the end of the array.
* For example, -2 refers to the second to last element of the array.
* `start` The beginning index of the specified portion of the array.
* If start is undefined, then the slice begins at index 0.
* `end` The end index of the specified portion of the array. This is exclusive of the element at the index 'end'.
* If end is undefined, then the slice extends to the end of the array.
* 배열 섹션의 복사본을 반환합니다.
* 시작과 끝 모두에 대해 음수 인덱스를 사용하여 배열 끝에서 오프셋을 나타낼 수 있습니다.
* 예를 들어 -2는 배열의 두 번째에서 마지막 요소를 나타냅니다.
* `start` 배열의 지정된 부분의 시작 인덱스입니다.
* 시작이 정의되지 않은 경우 슬라이스는 인덱스 0에서 시작합니다.
* `end` 배열에서 지정된 부분의 끝 인덱스입니다. 이것은 색인 'end'의 요소를 제외합니다.
* end가 정의되지 않은 경우 슬라이스는 배열의 끝까지 확장됩니다.

#### sort(compareFn?: (a: T, b: T) => number): this;
* Sorts an array in place.
* This method mutates the array and returns a reference to the same array.
* `compareFn` Function used to determine the order of the elements. It is expected to return
* a negative value if first argument is less than second argument, zero if they're equal and a positive
* value otherwise. If omitted, the elements are sorted in ascending, ASCII character order.
```ts
[11,2,22,1].sort((a, b) => a - b)
```
* 배열을 제자리에 정렬합니다.
* 이 메서드는 배열을 변경하고 동일한 배열에 대한 참조를 반환합니다.
* `compareFn` 요소의 순서를 결정하는 데 사용되는 함수. 돌아올 것으로 예상됩니다
* 첫 번째 인수가 두 번째 인수보다 작 으면 음수, 같으면 0, 양수
* 그렇지 않으면 값. 생략하면 요소가 ASCII 문자 오름차순으로 정렬됩니다.

#### splice(start: number, deleteCount?: number): T[];
* Removes elements from an array and, if necessary, inserts new elements in their place, returning the deleted elements.
* `start` The zero-based location in the array from which to start removing elements.
* `deleteCount` The number of elements to remove.
* `@returns` An array containing the elements that were deleted.
* 배열에서 요소를 제거하고 필요한 경우 새 요소를 그 자리에 삽입하여 삭제 된 요소를 반환합니다.
* `start` 요소 제거를 시작할 배열의 0부터 시작하는 위치입니다.
* `deleteCount` 제거 할 요소의 수입니다.
* `@returns` 삭제 된 요소를 포함하는 배열입니다.

#### splice(start: number, deleteCount: number, ...items: T[]): T[];
* Removes elements from an array and, if necessary, inserts new elements in their place, returning the deleted elements.
* `start` The zero-based location in the array from which to start removing elements.
* `deleteCount` The number of elements to remove.
* `items` Elements to insert into the array in place of the deleted elements.
* `@returns` An array containing the elements that were deleted.
* 배열에서 요소를 제거하고 필요한 경우 새 요소를 그 자리에 삽입하여 삭제 된 요소를 반환합니다.
* `start` 요소 제거를 시작할 배열의 0부터 시작하는 위치입니다.
* `deleteCount` 제거 할 요소의 수입니다.
* `items` 삭제 된 요소 대신 배열에 삽입 할 요소.
* `@ returns` 삭제 된 요소를 포함하는 배열입니다.

#### unshift(...items: T[]): number;
* Inserts new elements at the start of an array, and returns the new length of the array.
* `items` Elements to insert at the start of the array.
* 배열의 시작 부분에 새 요소를 삽입하고 배열의 새 길이를 반환합니다.
* `items` 배열의 시작 부분에 삽입 할 요소입니다.

#### indexOf(searchElement: T, fromIndex?: number): number;
* Returns the index of the first occurrence of a value in an array, or -1 if it is not present.
* `searchElement` The value to locate in the array.
* `fromIndex` The array index at which to begin the search. If fromIndex is omitted, the search starts at index 0.
* 배열에서 값이 처음 발견되는 인덱스를 반환하거나없는 경우 -1을 반환합니다.
* `searchElement` 배열에서 찾을 값입니다.
* `fromIndex` 검색을 시작할 배열 인덱스입니다. fromIndex가 생략되면 검색은 인덱스 0에서 시작합니다.

#### lastIndexOf(searchElement: T, fromIndex?: number): number;
* Returns the index of the last occurrence of a specified value in an array, or -1 if it is not present.
* `searchElement` The value to locate in the array.
* `fromIndex` The array index at which to begin searching backward. If fromIndex is omitted, the search starts at the last index in the array.
* 배열에서 지정된 값의 마지막 발생 인덱스를 반환하거나 존재하지 않는 경우 -1을 반환합니다.
* `searchElement` 배열에서 찾을 값입니다.
* `fromIndex` 뒤로 검색을 시작할 배열 인덱스입니다. fromIndex가 생략되면 배열의 마지막 인덱스에서 검색이 시작됩니다.

#### `every<S extends T>(predicate: (value: T, index: number, array: T[]) => value is S, thisArg?: any): this is S[];`
* Determines whether all the members of an array satisfy the specified test.
* `predicate` A function that accepts up to three arguments. The every method calls
* the predicate function for each element in the array until the predicate returns a value
* which is coercible to the Boolean value false, or until the end of the array.
* `thisArg` An object to which the this keyword can refer in the predicate function.
* If thisArg is omitted, undefined is used as the this value.
* 배열의 모든 멤버가 지정된 테스트를 충족하는지 여부를 결정합니다.
* `predicate` 최대 3 개의 인수를받는 함수입니다. 모든 메서드 호출
* 술어가 값을 리턴 할 때까지 배열의 각 요소에 대한 술어 함수
* 부울 값 false 또는 배열 끝까지 강제 변환 할 수 있습니다.
* `thisArg` this 키워드가 조건 자 함수에서 참조 할 수있는 객체입니다.
* thisArg를 생략하면 undefined가 이 값으로 사용됩니다. 

#### every(predicate: (value: T, index: number, array: T[]) => unknown, thisArg?: any): boolean;
* Determines whether all the members of an array satisfy the specified test.
* `predicate` A function that accepts up to three arguments. The every method calls
* the predicate function for each element in the array until the predicate returns a value
* which is coercible to the Boolean value false, or until the end of the array.
* `thisArg` An object to which the this keyword can refer in the predicate function.
* If thisArg is omitted, undefined is used as the this value.
* 배열의 모든 멤버가 지정된 테스트를 충족하는지 여부를 결정합니다.
* `predicate` 최대 3 개의 인수를받는 함수입니다. 모든 메서드 호출
* 술어가 값을 리턴 할 때까지 배열의 각 요소에 대한 술어 함수
* 부울 값 false 또는 배열 끝까지 강제 변환 할 수 있습니다.
* `thisArg` this 키워드가 조건 자 함수에서 참조 할 수있는 객체입니다.
* thisArg를 생략하면 undefined가 이 값으로 사용됩니다. 

#### some(predicate: (value: T, index: number, array: T[]) => unknown, thisArg?: any): boolean;
* Determines whether the specified callback function returns true for any element of an array.
* `predicate` A function that accepts up to three arguments. The some method calls
* the predicate function for each element in the array until the predicate returns a value
* which is coercible to the Boolean value true, or until the end of the array.
* `thisArg` An object to which the this keyword can refer in the predicate function.
* If thisArg is omitted, undefined is used as the this value.
* 지정된 콜백 함수가 배열의 모든 요소에 대해 true를 반환하는지 여부를 결정합니다.
* `predicate` 최대 3 개의 인수를받는 함수입니다. 일부 메서드 호출
* 술어가 값을 리턴 할 때까지 배열의 각 요소에 대한 술어 함수
* 부울 값 true 또는 배열 끝까지 강제 변환 할 수 있습니다.
* `thisArg` this 키워드가 조건 자 함수에서 참조 할 수있는 객체입니다.
* thisArg를 생략하면 undefined가 이 값으로 사용됩니다. 

#### forEach(callbackfn: (value: T, index: number, array: T[]) => void, thisArg?: any): void;
* Performs the specified action for each element in an array.
* `callbackfn`  A function that accepts up to three arguments. forEach calls the callbackfn function one time for each element in the array.
* `thisArg`  An object to which the this keyword can refer in the callbackfn function. If thisArg is omitted, undefined is used as the this value.

#### `map<U>(callbackfn: (value: T, index: number, array: T[]) => U, thisArg?: any): U[];`
* Calls a defined callback function on each element of an array, and returns an array that contains the results.
* `callbackfn` A function that accepts up to three arguments. The map method calls the callbackfn function one time for each element in the array.
* `thisArg` An object to which the this keyword can refer in the callbackfn function. If thisArg is omitted, undefined is used as the this value.
* 배열의 각 요소에 대해 정의 된 콜백 함수를 호출하고 결과를 포함하는 배열을 반환합니다.
* `callbackfn` 최대 3 개의 인수를받는 함수입니다. map 메서드는 배열의 각 요소에 대해 callbackfn 함수를 한 번 호출합니다.
* `thisArg` this 키워드가 callbackfn 함수에서 참조 할 수있는 객체입니다. thisArg가 생략되면 undefined가 이 값으로 사용됩니다.

#### `filter<S extends T>(predicate: (value: T, index: number, array: T[]) => value is S, thisArg?: any): S[];`
* Returns the elements of an array that meet the condition specified in a callback function.
* `predicate` A function that accepts up to three arguments. The filter method calls the predicate function one time for each element in the array.
* `thisArg` An object to which the this keyword can refer in the predicate function. If thisArg is omitted, undefined is used as the this value.
* 콜백 함수에 지정된 조건을 충족하는 배열 요소를 반환합니다.
* `predicate` 최대 3 개의 인수를받는 함수입니다. 필터 메소드는 배열의 각 요소에 대해 한 번 술어 함수를 호출합니다.
* `thisArg` this 키워드가 조건 자 함수에서 참조 할 수있는 객체입니다. thisArg가 생략되면 undefined가 이 값으로 사용됩니다.

#### filter(predicate: (value: T, index: number, array: T[]) => unknown, thisArg?: any): T[];
* Returns the elements of an array that meet the condition specified in a callback function.
* `predicate` A function that accepts up to three arguments. The filter method calls the predicate function one time for each element in the array.
* `thisArg` An object to which the this keyword can refer in the predicate function. If thisArg is omitted, undefined is used as the this value.
* 콜백 함수에 지정된 조건을 충족하는 배열 요소를 반환합니다.
* `predicate` 최대 3 개의 인수를받는 함수입니다. 필터 메소드는 배열의 각 요소에 대해 한 번 술어 함수를 호출합니다.
* `thisArg` this 키워드가 조건 자 함수에서 참조 할 수있는 객체입니다. thisArg가 생략되면 undefined가 이 값으로 사용됩니다.

#### reduce(callbackfn: (previousValue: T, currentValue: T, currentIndex: number, array: T[]) => T): T;
#### reduce(callbackfn: (previousValue: T, currentValue: T, currentIndex: number, array: T[]) => T, initialValue: T): T;
* Calls the specified callback function for all the elements in an array. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.
* `callbackfn` A function that accepts up to four arguments. The reduce method calls the callbackfn function one time for each element in the array.
* `initialValue` If initialValue is specified, it is used as the initial value to start the accumulation. The first call to the callbackfn function provides this value as an argument instead of an array value.
* 배열의 모든 요소에 대해 지정된 콜백 함수를 호출합니다. 콜백 함수의 반환 값은 누적 된 결과이며 콜백 함수에 대한 다음 호출에서 인수로 제공됩니다.
* `callbackfn` 최대 4 개의 인수를받는 함수입니다. reduce 메서드는 배열의 각 요소에 대해 callbackfn 함수를 한 번 호출합니다.
* `initialValue` initialValue를 지정하면 누적을 시작하는 초기 값으로 사용됩니다. callbackfn 함수에 대한 첫 번째 호출은 이 값을 배열 값 대신 인수로 제공합니다. 

#### `reduce<U>(callbackfn: (previousValue: U, currentValue: T, currentIndex: number, array: T[]) => U, initialValue: U): U;`
* Calls the specified callback function for all the elements in an array. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.
* `callbackfn` A function that accepts up to four arguments. The reduce method calls the callbackfn function one time for each element in the array.
* `initialValue` If initialValue is specified, it is used as the initial value to start the accumulation. The first call to the callbackfn function provides this value as an argument instead of an array value.

#### `reduceRight(callbackfn: (previousValue: T, currentValue: T, currentIndex: number, array: T[]) => T): T;`
#### `reduceRight(callbackfn: (previousValue: T, currentValue: T, currentIndex: number, array: T[]) => T, initialValue: T): T;`
* Calls the specified callback function for all the elements in an array, in descending order. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.
* `callbackfn` A function that accepts up to four arguments. The reduceRight method calls the callbackfn function one time for each element in the array.
* `initialValue` If initialValue is specified, it is used as the initial value to start the accumulation. The first call to the callbackfn function provides this value as an argument instead of an array value.

####  `reduceRight<U>(callbackfn: (previousValue: U, currentValue: T, currentIndex: number, array: T[]) => U, initialValue: U): U;`

    [n: number]: T;

* Calls the specified callback function for all the elements in an array, in descending order. The return value of the callback function is the accumulated result, and is provided as an argument in the next call to the callback function.
* `callbackfn` A function that accepts up to four arguments. The reduceRight method calls the callbackfn function one time for each element in the array.
* `initialValue` If initialValue is specified, it is used as the initial value to start the accumulation. The first call to the callbackfn function provides this value as an argument instead of an array value.


```ts
interface ArrayConstructor {
    new(arrayLength?: number): any[];
    new <T>(arrayLength: number): T[];
    new <T>(...items: T[]): T[];
    (arrayLength?: number): any[];
    <T>(arrayLength: number): T[];
    <T>(...items: T[]): T[];
    isArray(arg: any): arg is any[];
    readonly prototype: any[];
}

declare var Array: ArrayConstructor;
```