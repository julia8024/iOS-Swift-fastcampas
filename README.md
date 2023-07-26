<details>
<summary><h3>목차</h3></summary>
<div markdown="1">

  &emsp; [1. Swift 기본 문법](#1-swift-기본-문법)<br>
  &emsp; [2. 명언 생성기 앱 만들기](#2-명언-생성기-앱-만들기)<br>
</div>
</details>

## 1. Swift 기본 문법

### 상수와 변수
- let 키워드로 선언된 상수는 값 변경 불가
  - 변하면 안되는 값을 let으로 선언
<br>

```Swift
import Foundation

// 상수
// let 상수명: 데이터 타입 = 값
let a: Int = 100

// 변수
// var 변수명: 데이터 타입 = 값
var b: Int = 200
```
<br>

### 데이터 타입
| 타입 | 설명 | 타입 | 설명 |
|---|---|---|---|
| int | 64bit 정수형 | Bool | true, false 값 |
| UInt | 부호가 없는 64bit 정수형 | Character | 문자 |
| Float | 32bit 부동 소수점 | String | 문자열 |
| Double | 64bit 부동 소수점 | Any | 모든 타입을 지칭하는 키워드 |

<br>

```Swift
import Foundation

// Int
var someInt: Int = -100
someInt = 100

// UInt
var someUInt: UInt = 200

// Float
var someFloat: Float = 1.1
someFloat = 1
print(someFloat)
// 출력 : "1.0\n"

// Double
var someDouble: Double = 1.1
someDouble = 1

// Bool
var someBool: Bool = true
someBool = false

// Character
var someCharacter: Character = "가"
someCharacter = "A"
someCharacter = "⭐️"

// String
var someString: String = "안녕하세요 😁"

// 타입 추론: Int
// 타입 생략 가능
var number = 10
```
<br>

### 컬렉션 타입
| 타입 | 설명 |
|---|---|
| Array | 데이터 타입의 값들을 순서대로 저장하는 리스트 |
| Dictionary | 순서없이 키(key)와 값(value) 한 쌍으로 데이터를 저장하는 컬렉션 타입 |
| Set | 같은 데이터 타입의 값을 순서없이 저장하는 리스트 |
<br>

> 배열
```Swift
// 빈 배열 생성
var numbers: Array<Int> = Array<Int>() // []

// 값 추가
numbers.append(1) // [1]
numbers.append(2) // [1,2]
numbers.append(3) // [1,2,3]

// 값 참조
numbers[0] // 1
numbers[1] // 2

// 값 삽입
numbers.insert(4, at: 2) // [1,2,4,3]
numbers // [1,2,4,3]

// 값 삭제
numbers.remove(at: 0) // 1
numbers // [2,4,3]


// 배열 생성 방법 (3가지)
var arr1: Array<Int> = Array<Int>()
var arr2 = [String]()
var arr3: [String] = []
```
<br>

> 딕셔너리
```Swift
// 딕셔너리 생성
var dic: Dictionary<String, Int> = Dictionary<String, Int>() // [:]

// 값 추가
dic["alice"] = 3
dic["bob"] = 5
dic // ["bob": 5, "alice": 3]

// 값 변경
dic["alice"] = 6
dic // ["bob": 5, "alice": 6]

// 값 삭제
dic.removeValue(forKey: "alice")
dic // ["bob": 5]


// 딕셔너리 생성 방법 (2가지)
var dic1: Dictionary<String, Int> = Dictionary<String, Int>()
var dic2: [String: Int] = [:]
```
<br>

> set
```Swift
// set 생성
var set: Set = Set<Int>() // Set([])

// 값 삽입
set.insert(10)
set.insert(20)
set.insert(30) // (inserted true, memberAfterInsert 30)
set.insert(30) // (inserted false, memberAfterInsert 30)
set.insert(30)
set // {20, 30, 10}
// 순서 X, 중복 X

set.remove(20)
set // {30, 10}
```
<br>

### 함수 사용법
- 함수 : 작업의 가장 작은 단위이자 코드의 집합
```Swift
import Foundation

/*
 func 함수명(파라미터_이름: 데이터_타입) -> 반환_타입 {
     return 반환_값
 }
 */

func sum(a: Int, b: Int) -> Int {
    return a+b
}

sum(a: 5, b: 3) // 8

// 매개변수가 없는 함수
func hello() -> String {
    return "hello"
}

hello() // "hello"

// 반환값이 없는 함수
func printName() -> Void {
}

func printName2() {
}

func greeting(friend: String, me: String = "gunter") {
    print("Hello, \(friend)! I'm \(me)")
}

greeting(friend: "Albert") // "Hello, Albert! I'm gunter\n"

/*
 func 함수명(전달인자_레이블: 매개변수_이름: 매개변수_타입, 전달인자_레이블: 매개변수_이름: 매개변수_타입 ...) -> 반환 타입 {
     return 반환_값
 }
 */

func sendMessage(from myName: String, to name: String) -> String {
    return "Hello \(name)! I'm \(myName)"
}

sendMessage(from: "Gunter", to: "Json") // "Hello Json! I'm Gunter"

// _ : 와일드카드 식별자
func sendMessage(_ name: String) -> String {
    return "Hello \(name)"
}

sendMessage("alice") // "Hello alice"

// 가변 매개변수
// 함수마다 가변 매개변수는 1개만 가질 수 있음
func sendMessage(me: String, friends: String...) -> String {
    return "Hello \(friends)! I'm \(me)"
}

sendMessage(me: "Gunter", friends: "Json", "Alice", "Bob")
// "Hello ["Json", "Alice", "Bob"]! I'm Gunter"
```
<br>

### 조건문
```Swift
import Foundation

var age = 12

// if문
if age < 19 {
    print("미성년자 입니다.")
}
// 미성년자 입니다.


age = 20
// if-else 문
if age < 19 {
    print("미성년자")
} else {
    print("성인")
}
// 성인


// if - else if - else
let animal = "cat"

if animal == "dog" {
    print("강아지 사료 주기")
} else if animal == "cat" {
    print("고양이 사료 주기")
} else {
    print("해당하는 동물 사료가 없음")
}
// 고양이 사료 주기


// switch
let color = "green"

switch color {
case "blue":
    print("파란색")
case "green":
    print("초록색")
case "yellow":
    print("노란색")
default:
    print("찾는 색상 없음")
}
// 초록색


let temperature = 30

switch temperature {
case -20...9:
    print("겨울")
case 10...14:
    print("가을")
case 15...25:
    print("봄")
case 26...35:
    print("여름")
default:
    print("이상 기후")
}
// 여름
```
<br>

### 반복문
```Swift
import Foundation

/*
 for 루프상수 in 순회대상 {
    // 실행할 구문..
 }
 */

for i in 1...4 {
    print(i)
}
// 1 \n 2 \n 3 \n 4

let array = [1,2,3,4,5]

for i in array {
    print(i)
}
// 1 \n 2 \n 3 \n 4 \n 5

/*
 while 조건식 {
    // 실행할 구문
 }
 */

var number = 5

while number < 10 {
    number += 1
}

number // 10


/*
 repeat {
    // 실행할 구문
 } while 조건식
 */

var x = 6
repeat {
    x += 2
} while x < 5

print(x) // 8
```
<br>

### 옵셔널
- 값이 있을수도 있고 없을수도 있음
```Swift
var name: String? = nil
var num: Int? = nil
```
```Swift
import Foundation

var name: String? // nil

var optionalName: String? = "Gunter"
print(optionalName) // Optional("Gunter")
```
<br>

### 옵셔널 바인딩
- 옵셔널 해제 방법
| 명시적 해제 | 묵시적 해제 |
|---|---|
| 강제 해제 | 컴파일러에 의한 자동 해제 |
| 비강제 해제(옵셔널 바인딩) | 옵셔널의 묵시적 해제 |
<br>

```Swift
import Foundation

var number: Int? = 3
print(number) // Optional(3)
// 강제 해제
print(number!) // 3
// nil인 경우 오류나서 프로그램이 강제종료될 수 있음
// 위험!

// 비강제 해제
if let result = number {
    print(result) // 3
} else {
}

// guard문을 통해 해제
func test() {
    let number: Int? = 5
    guard let result = number else { return }
    print(result)
}

test() // 5

// 묵시적 해제
let value: Int? = 6
if value == 6 {
    print("value가 6입니다")
} else {
    print("value가 6이 아닙니다")
}
// 출력 : value가 6입니다
// 비교연산을 수행하면 옵셔널이 자동으로 해제되어 비교연산 수행


let string = "12"
// string to int는 옵셔널로 선언되어야 함
// Int? 를 Int!로 선언하면 묵시적 해제
var stringToInt: Int! = Int(string)
print(stringToInt + 1) // 13
```




<hr>
<br>

## 2. 명언 생성기 앱 만들기

### Cocoa touch Framework
<img src="https://github.com/julia8024/julia8024/assets/79641953/829780ca-b9b9-4f61-af14-5db2b1185773" width="30%">
<br><br><br>

### UIKit
![image](https://github.com/julia8024/julia8024/assets/79641953/4367c33b-6305-41ba-b2bd-e3e5737fb378)
<br><br><br>

### MVC 디자인 패턴
- 애플의 MVC 패턴에서는 View와 Controller를 분리하기 어려움
  - View와 Controller가 너무 강하게 연결되어있어, ViewController가 거의 모든 일을 담당함
  - ViewController에서는 Controller가 View의 라이프사이클에 관여함
  <br>→ 프로젝트 규모가 커질수록 Controller가 비대해지고 내부 구조가 복잡해져 유지보수가 어려워짐
  <br>&emsp; 따라서 이러한 단점을 해결하기 위해 MVVM이나 VIPER 패턴 등을 활용
<br><br>

### UIView
- 화면의 직사각형 영역에 대한 내용을 관리하는 개체
<br><br>

### ViewController
- 앱의 근간을 이루는 객체로 모든 앱은 최소한 하나 이상의 뷰 컨트롤러를 가짐
- 주요 역할
    - 데이터 변화에 따라 view 콘텐츠를 업데이트
    - view들과 함께 사용자 상호작용에 응답
    - view를 리사이징하고 전체적인 인터페이스의 레이아웃 관리
    - 다른 뷰컨트롤러들과 함께 앱 구성
<br><br>

### AutoLayout
- 제약 조건(Constraints)을 이용해서 뷰의 위치를 지정하는 것
- 아이폰의 다양한 해상도 비율에 대응하기 위해 나온 개념
- 세로보기, 가로보기 화면 모두 지원
<br><br>

### Storyboard
- iOS 앱의 사용자 인터페이스를 시각적으로 표현하여 컨텐츠 화면과 화면 간의 연결을 보여주는 도구
- Scene으로 구성되며, 각 Scene은 View와 ViewController를 나타냄
<br><br>

### 🖋️ 명언생성기 App
```swift
import UIKit

class ViewController: UIViewController {
    
    @IBOutlet weak var quoteLabel: UILabel!
    @IBOutlet weak var nameLabel: UILabel!
    
    let quotes = [
        Quote(contents: "죽음을 두려워하는 나머지 삶을 시작조차 못하는 사람이 많다.", name: "벤다이크"),
        Quote(contents: "나는 나 자신을 빼 놓고는 모두 안다.", name: "비용"),
        Quote(contents: "편견이란 실효성이 없는 의견이다.", name: "암브로스 빌"),
        Quote(contents: "분노는 바보들의 가슴속에서만 살아간다.", name: "아인슈타인"),
        Quote(contents: "몇 번이라도 좋다! 이 끔찍한 세상이여...다시!", name: "니체")
    ]
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }

    @IBAction func tapQuoteGeneratorButton(_ sender: Any) {
        // 0~4 사이의 난수 생성
        let random = Int(arc4random_uniform(5))
        let quote = quotes[random]

        self.quoteLabel.text = quote.contents
        self.nameLabel.text = quote.name
    }
    
}

```

