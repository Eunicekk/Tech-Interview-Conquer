<details>
  <summary><strong> RAG(검색 증강 생성)란 무엇인지 설명해주세요. </strong></summary>

  ### 개념

  RAG (Retrieval-Augmented Generation)는 자연어 처리(NLP)에서 정보 검색(Retrieval)과 생성(Generation)을 결합한 프레임워크입니다.
  RAG는 GPT-3와 같은 대규모 언어 모델(Large Language Models, LLMs)과 외부 지식 소스(데이터베이스, 문서 저장소 등등)를 통합하여 더 정확하고 맥락에 맞는 답변을 생성합니다.

</details>

<details>
  <summary><strong> RAG의 주요 단계 두 가지를 설명해주세요. </strong></summary>

  1. Retrieval (정보 검색 단계)
    
    - 모델이 답변을 생성하기 전에 외부 데이터 소스에서 관련 정보를 검색합니다.
    - 이 과정은 대개 쿼리(query)를 기반으로 수행되며, 검색 엔진이나 벡터 검색을 사용합니다.
    - 검색된 문서나 텍스트 조각들이 생성 모델에 컨텍스트로 제공됩니다.
     
  2. Augmented Generation (생성 단계)
    
    - 검색된 정보를 기반으로, 생성 모델이 보다 정교하고 사실에 기반한 답변을 생성합니다.
    - 이 단계에서 모델은 기존 LLM의 능력(문맥 이해, 유창한 문장 생성)을 활용하여 자연스러운 텍스트를 생성합니다.
    

</details>

<details>
  <summary><strong> RAG의 장점에 대해 설명해주세요. </strong></summary>

  1. 사실성 개선
  - LLM은 자체적으로 훈련된 데이터만 활용하므로 정보가 오래되거나 부정확할 수 있습니다.
  - 외부 검색을 통합하면 최신 정보와 정확한 데이터를 반영할 수 있습니다.

  2. 확장성
  - 모델의 크기를 키우지 않고도, 다양한 도메인에 대한 질문에 답할 수 있습니다. 이는 외부 데이터 소스를 적절히 활용하는 것으로 가능합니다.
  
  3. 유연성
  - 다양한 검색 및 생성 알고리즘과 통합할 수 있습니다. 

</details>
