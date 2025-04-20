# React의 LifeCycle

---

## 면접 질문 예시

> "리액트의 라이프사이클에 대해 설명해 주세요”

---

<details>
  <summary><h2> 평가 요소 및 모범 답안</h2></summary>

  ### 1. 클래스 컴포넌트 라이프사이클
  - 포함내용
    * Mounting (컴포넌트 생성 시)
      - constructor()
      - static getDerivedStateFromProps()
      - render()
      - componentDidMount() ← 주로 API 호출이나 구독 설정에 사용
    * Updating (props, state 변경 시)
      - static getDerivedStateFromProps()
      - shouldComponentUpdate() ← 리렌더링 성능 최적화
      - render()
      - getSnapshotBeforeUpdate() ← 렌더 직전 DOM 상태 캡처
      - componentDidUpdate() ← 데이터 리페치 등
    * Unmounting (컴포넌트 제거 시)
      - componentWillUnmount() ← 구독 해제, 타이머 클리어 등에 사용
     
  ### 2. 함수형 컴포넌트에서의 라이프사이클
  - 포함내용
    * useEffect(() => { ... }, [])
      - componentDidMount 역할
      - 마운트 시 1회 실행
    * useEffect(() => { ... })
      - componentDidUpdate 역할
      - 마운트 및 업데이트 시 실행
    * useEffect(() => { return () => { ... } }, [])
      - componentWillUnmount 역할
      - 언마운트 시 실행
    * useLayoutEffect
      - DOM 변경이 브라우저에 반영되기 전에 동기적으로 실행됨
      - getSnapshotBeforeUpdate와 유사한 시점
  
  ### 3.모범 답안 예시

  > 리액트 컴포넌트의 라이프사이클은 크게 마운트(Mount), 업데이트(Update), 언마운트(Unmount) 세 단계로 나뉩니다.<br />
  > Mount 시 constructor → getDerivedStateFromProps → render → componentDidMount 순으로 호출되며, 보통 API 호출이나 이벤트 구독은 componentDidMount에서 처리합니다.<br />
  > Update 시에는 getDerivedStateFromProps → shouldComponentUpdate → render → getSnapshotBeforeUpdate → componentDidUpdate가 실행되고, DOM 업데이트 이후 후처리를 할 수 있습니다.<br />
  > Unmount 시에는 componentWillUnmount가 호출되어 정리 작업을 수행합니다.<br />
  > 함수형 컴포넌트에서는 useEffect 훅을 통해 라이프사이클을 흉내낼 수 있습니다.<br />
  
</details>
