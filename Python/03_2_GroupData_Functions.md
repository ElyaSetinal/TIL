## **각 그룹형 데이터들의 함수 목록 정리**

### *String*

| 함수명 | 동작 | 함수 내부 요소 | 작성 방법 |
| --- | --- | --- | --- |
| count() | 내부 요소가 나오는 횟수 반환 | 문자열 | Var.count('a') |
| lower() | 전부 소문자로 변환 |  | Var.lower() |
| upper() | 전부 대문자로 변환 |  | Var.upper() |
| lstrip() | 왼쪽 공백/문자열 제거 | 문자열(o) | Var.lstrip('a') |
| rstrip() | 오른쪽 공백/문자열 제거 | 문자열(o) | Var.rstrip('a') |
| strip() | 양 쪽 공백/문자열 제거 | 문자열(o) | Var.strip('a') |
| replace() | 문자열 교체 | old 문자열, new 문자열 | Var.replace('a', 'b') |
| split() | 요소를 분리하여 리스트로 반환 | 문자열 | Var.split('a') |
| find() | 범위내 특정 문자열의 최초 idx 반환 | 검색 대상, 시작idx(o, default=0), 끝idx(o, default=-1) | Var.find('a', 2, 8) |
| join() | 결합하여 하나의 문자열로 반환 | Iterable Data | "a".join('bcd') |
| center() | 지정 길이만큼 늘리고 문자열을 중앙 정렬 | int, 문자열(o) | Var.center(10, '-') |
| ljust() | 지정 길이만큼 늘리고 문자열을 좌측 정렬 | int, 문자열(o) | Var.ljust(10, '-') |
| rjust() | 지정 길이만큼 늘리고 문자열을 우측 정렬 | int, 문자열(o) | Var.rjust(10, '-') |

<br>

### *List*
| 함수명 | 동작 | 함수 내부 요소 | 작성 방법 |
| --- | --- | --- | --- |
|append()|마지막에 데이터를 추가|data| Var.append() |
|insert()|지정된 idx에 데이터를 추가|idx, data| Var.insert() |
|extend()|데이터 병합|data| Var.extend() |
|pop()|마지막 혹은 지정 idx의 값을 추출하여 반환|idx(o)| Var.pop(3) |
|remove()|해당 값 제거, 없으면 에러발생|data| Var.remove() |
|del list[]|해당 idx의 값을 삭제|idx| del list[2] |
|clear()|모든 요소 삭제|| Var.clear() |
|count()|해당 값 갯수 반환|value| Var.count() |
|index()|해당 값의 최초 idx 반환|value| Var.index() |
|reverse()|리스트 순서를 뒤집는다.|| Var.reverse() |
|reversed()|원본을 유지한 상태로 순서를 뒤집어서 반환. 변수 필요|list| New_Var = Var.reversed() |
|sort()|리스트를 정렬|key=(o,default=None), reverse=(o,default=False)| Var.sort() |
|sorted()|원본을 유지한 상태로 리스트를 정렬하여 반환. 변수 필요|list, key=(o,default=None), reverse=(o,default=False) | New_Var = Var.sorted() |


<br>

### *Tuple*
| 함수명 | 동작 | 함수 내부 요소 | 작성 방법 |
| --- | --- | --- | --- |
|count()|해당 데이터의 개수를 반환|data|Var.count()|
|index()|해당 데이터의 최초 idx를 반환|data|Var.index()|

<br>

### *Set*
| 함수명 | 동작 | 함수 내부 요소 | 작성 방법 |
| --- | --- | --- | --- |
|add()|집합에 요소 추가|data|Var.add()|
|update()|요소 병합|Iterable|Var.update()|
|discard()|해당 값 삭제, 없으면 미동작|value|Var.discard(2)|
|remove()|해당 값 삭제, 없으면 에러발생|value|Var.remove(2)|
|pop()|랜덤한 값 추출||Var.pop()|
|union()|두 집합의 합집합 반환|set|Set1.union(Set2)|
|intersection()|두 집합의 교집합 반환|set|Set1.intersection(Set2)|
|difference()|두 집합의 차집합 반환|set|Set1.difference(Set2)|
|symmetric_difference()|두 집합의 대칭 차집합 반환|set|Set1.symmetric_difference(Set2)|

<br>

### *Dict*

> 함수가 아닌 것에 대해선 *을 추가

| 함수명 | 동작 | 함수 내부 요소 | 작성 방법 |
| --- | --- | --- | --- |
|*[New_key]=value|새로운 key:value를 추가||Var[New_key] = Value|
|*[key]=New_value|기존 key에 값 변경||Var[key] = New_Value|
|del Var[key]|해당 키와 값을 제거||del Var[key]|
|pop()|해당 키:값을 추출하여 반환, message가 있으면 error대신 message 반환|key, message(o)|Var.pop(key, message)|
|clear()|모든 요소 삭제||Var.clear()|
|update()|두 dict 병합|dict|dict1.update(dict2)|
|keys()|key들을 반환||Var.keys()|
|values()|value들을 반환||Var.values()|
|items()|key,value를 튜플로써 반환||Var.items()|
