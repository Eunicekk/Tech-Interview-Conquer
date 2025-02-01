<details>
  <summary><strong>Git Fork와 Git Clone의 차이점은 무엇인가요?</strong></summary>

  Git Fork는 GitHub 상에서 원본 저장소를 자신의 계정으로 복제하는 작업이며, 원본과 독립적으로 관리됩니다.  
  반면, Git Clone은 로컬 환경에 저장소를 복사하는 명령으로, Fork 없이도 원본 저장소를 로컬로 클론할 수 있습니다.  
  Fork는 주로 오픈소스 프로젝트에 기여하거나 별도의 작업이 필요한 경우 사용됩니다.
</details>

<details>
  <summary><strong>Fork한 저장소를 원본 저장소와 동기화하려면 어떻게 해야 하나요?</strong></summary>

  Fork한 저장소를 원본 저장소와 동기화하려면 업스트림(upstream) 리모트를 설정해야 합니다.  
  이를 위해 git remote add upstream <original-repo-url> 명령을 사용해 업스트림을 추가하고, git fetch upstream으로 원본의 변경 사항을 가져옵니다.  
  그런 다음, git merge upstream/main을 실행해 변경 사항을 병합할 수 있습니다.
</details>

<details>
  <summary><strong>원본 저장소의 변경 사항을 Fork한 저장소로 반영하지 않으면 어떤 문제가 발생하나요?</strong></summary>

  원본 저장소의 변경 사항을 반영하지 않으면 Fork한 저장소와 원본 저장소 간에 버전 충돌이 발생할 가능성이 높아집니다.  
  특히, 원본 저장소가 활발히 업데이트되는 경우, 변경된 구조나 코드를 반영하지 않으면 Pull Request를 보낼 때 병합 충돌이 발생할 수 있습니다.  
  이를 방지하려면 주기적으로 원본 저장소를 동기화해야 합니다.
</details>