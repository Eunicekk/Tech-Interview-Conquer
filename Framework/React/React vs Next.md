<details>
  <summary><strong>React 대신 Next를 쓰는 이유는 무엇인가?</strong></summary>

<br>

## Next

- full-stack React **Framework**
- 파일 기반 라우팅 지원 → 프로젝트 폴더명이 url 경로로 들어가게 된다.
![image](https://github.com/user-attachments/assets/a8896844-78f2-487c-9292-346d80a6263e)
http://localhost:3001/about-us/company/sales 로 연결
- SSR 우선시 하지만, SSG 또는 CSR 사용 가능 (혼합 가능)
- React 최신 기술을 반영 = 이 때문에 안정성 이슈가 생길 수 있음
- React + Vite에 비해서 오버헤드 / 안정성 / 유지보수성에 러닝커브가 높음
- hydration(렌더링 동작원리)에서 Next는 클라이언트 응답 전 서버에서 모든 page와 component를 렌더링 후 전닳
- 미리보기 화면이 필요한 서비스나 SEO 활용이 필요한 서비스는 Next.js를 고려


## React

- JavaScript 기반 **라이브러리**
- 빌드를 위해서 CRA(Create React App)보다 Vite를 추천
- Vite + React 사용했을 때 SPA/CSR을 우선시하고, 프레임워크 지원이 없고, RSC(React Serverer Component)를 사용할 수 없음


</details>
