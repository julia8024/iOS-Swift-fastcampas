<details>
<summary><h3>목차</h3></summary>
<div markdown="1">

  &emsp; 1. Swift 기본 문법<br>
  &emsp; 2. 명언 생성기 앱 만들기<br>
</div>
</details>

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

