<details>
  <summary><strong>Checked Exception과 Unchecked Exception에 대해서 설명해 주세요</strong></summary>
  
<br>

**Checked Exception**은 컴파일 시점에 처리해야 하는 예외로 대표적으로 IOException, ClassNotFoundException 등이 있습니다  
이는 예측 가능한 오류 상황(IO, DB 등 외부 환경)을 강제적으로 처리해야 하는 오류입니다(throws, try/catch 등)   
**Unchecked Exception**(Runtime Exception 하위 클래스)은 런타임에 발생하는 예외로 대표적으로 NullPointerException, ArrayIndexOutOfBoundsException 등이 있습니다  
이는 일반적으로 프로그래밍 로직, 개발자 실수으로 인해 발생하는 오류로 강제적으로 처리하지 않아도 됩니다  
이 **두 가지를 나누는 이유**는 개발자가 예측 가능한 오류를 놓치지 않도록 도우면서, 로직상의 오류는 강제하지 않으므로 개발의 편의성(모든 코드에 try/catch 문을 사용할 필요 없음)을 높이기 위해서 입니다.

</details>
