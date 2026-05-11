# 도쿄일렉트론코리아 RAG 교육
## 기초 과정 (24H)

`RAG 파이프라인 구축부터 프로덕션 배포까지` 기초 과정 실습 저장소입니다.

이 저장소는 **기초 과정 3일 코스**와 3일차에 진행하는 **미니 RAG 경진대회** 자료를 담고 있습니다.

## 과정 소개

이 과정은 특정 서비스에 종속되지 않는 오픈소스 프레임워크를 바탕으로, RAG 파이프라인의 기본 구조를 이해하고 직접 구현하는 데 초점을 둡니다.

- 프롬프트 엔지니어링과 LangChain 기반 기본 RAG 파이프라인 구성
- 문서 파싱, 청킹, 임베딩, 벡터 검색, 벡터 저장소 설계 이해
- 질문 변환(Query Transformation), 하이브리드 검색(Hybrid Retrieval), 재정렬(Re-ranking), 문맥 정제로 검색 품질 개선
- 검색 성능과 답변 품질을 나누어 평가하는 RAG 성능 평가(RAGAS/TruLens)
- 운영 모니터링과 실행 추적을 통한 RAG 파이프라인 점검(Langfuse, TruLens 역할 포함)
- 온톨로지와 지식그래프 기반 Graph RAG 기초 이해

## 교육 목표

- RAG 파이프라인의 핵심 구조인 임베딩, 벡터 검색, 청킹을 이해하고 직접 구현합니다.
- LangChain 기반 기본 RAG 시스템을 구축하고, 품질 개선 포인트를 단계별로 설명할 수 있게 합니다.
- 자동 평가 프레임워크 기반 평가 흐름(RAGAS)을 익히고, 미니 RAG 경진대회에서 정답률 개선 과정을 직접 실험합니다.

## 3일 커리큘럼

### 1일차

- 실습 환경 구성: 필수 라이브러리 설치, API 키 설정
- LangChain 기본 구조와 체인 구성 방식 이해
- 프롬프트 엔지니어링 기초: 역할 메시지, PromptTemplate/ChatPromptTemplate, Few-shot 방식
- Q&A 챗봇 구현과 체인 실행 방식(LCEL) 비교: `invoke`, `ainvoke`, `batch`, `stream`
- RAG 기본 개념: LLM의 한계, 검색과 생성의 결합
- 의미 기반 검색 이해: 임베딩, 검색기, 벡터 유사도
- 벡터 저장소 구축과 검색 실습: ChromaDB 기반 저장, 검색, 영속화
- 벡터 DB와 검색 엔진 선택 기준 비교: ChromaDB, FAISS, Qdrant, Milvus, Pinecone
- 벡터 인덱싱 기법 이해: HNSW를 포함한 주요 인덱스 방식
- 문서 처리 파이프라인: PDF 파싱, 문서 분할, 벡터 인덱스 구축
- 기본 RAG 파이프라인 구현과 일반 LLM 답변 비교
- Naive RAG의 한계와 개선 지점 진단
- 청킹 전략 비교: 고정 길이, 재귀적 분할, 구조 기반 청킹, 시맨틱 청킹
- 질문 재작성(Query Rewriting) 기반 검색 전 최적화

### 2일차

- 기본 RAG 흐름 복습과 검색 품질 개선 방향 정리
- 질문 확장 전략: 하나의 질문을 여러 검색 표현으로 확장(Multi-Query Retrieval)
- 복합 질문 처리 관점: 질문 확장과 질문 분해(Query Decomposition)의 차이
- 가상 답변 기반 검색: 질문을 문서에 가까운 표현으로 바꿔 검색(HyDE)
- Semantic Routing / RAG 라우팅: 가진 문서로 답할 질문만 벡터DB 검색, 범위 밖 질문은 검색 생략
- 검색 방식 비교: 의미 기반 검색(Dense Retrieval)과 키워드 기반 검색(BM25 Sparse Retrieval)
- 하이브리드 검색 설계: 의미 기반 검색과 키워드 검색 결합(Hybrid Retrieval)
- 검색 결과 결합 전략: 병렬 검색과 순위 기반 결합(RRF, Reciprocal Rank Fusion)
- 하이브리드 검색 결과 비교 실험
- 후보 문서 품질 개선: 검색 결과 재정렬(Re-ranking)
- 정밀 재정렬 실습: 질문-문서 쌍 기반 관련도 판단(Cross-Encoder Re-ranking)
- 검색 후 문맥 정제: 필터링과 압축 단계 이해(Context Filtering & Compression)
- 중복 제거를 통한 검색 문맥 품질 개선(Deduplication)
- 문맥 압축 전략: 원문 추출형과 요약 생성형 방식(Extractive / Abstractive Compression)
- 질문 기준 문맥 압축 실습
- 다중 표현 인덱싱: 검색 단위와 반환 단위 분리(Multi-Representation Indexing)

### 3일차

- 평가셋 설계: 질문, 기준 답변, 관련 근거 청크 정의
- 검색 성능 평가: 필요한 근거를 상위 결과에서 찾았는지 측정(Hit@K, Recall@K)
- 검색 전략별 정량 비교: 의미 기반, 키워드 기반, 하이브리드 검색 비교
- 검색 결과 상세 로그 분석
- 답변 품질 평가: 검색 문맥에 근거한 답변인지 확인(Faithfulness)
- LLM 기반 자동 채점으로 답변 근거성 평가(LLM-as-a-Judge)
- RAG 자동 평가 프레임워크 이해: 입력 구조와 평가 지표(RAGAS)
- 자동 평가 프레임워크 기반 평가 실행과 점수 해석(RAGAS: LLMContextRecall, Faithfulness, FactualCorrectness)
- 운영 모니터링과 실행 추적: 질문, 검색 문맥, 프롬프트, 모델 응답 흐름 확인(Langfuse trace)
- TruLens 기본 개념: Context Relevance, Groundedness, Answer Relevance feedback 구조
- 평가 도구와 관찰 도구의 역할 구분: 평가셋 기반 평가, 실행 추적, 피드백 계측(RAGAS, Langfuse, TruLens)
- 관계형 질문에서 벡터 검색이 흔들리는 지점 이해
- 지식 구조화 기초: 온톨로지, 엔터티, 관계, 트리플, 지식그래프
- LLM을 활용한 비정형 텍스트의 트리플 추출
- 온톨로지 기반 타입/관계 검증
- Graph RAG가 유리한 질문: 다단계 연결, 문서 간 엔터티 연결, 용어 정규화, 근거 경로 설명
- Graph RAG 설계 체크리스트
- 미니 RAG 경진대회를 통한 정답률 개선 실습

## 실습 환경

### 1. Anaconda 설치

Conda 기반 Python 가상환경을 사용하기 위해 Anaconda를 설치합니다.
아래 공식 페이지에서 운영체제(Windows / macOS / Linux)에 맞는 설치 파일을 내려받아 설치해 주세요.

Anaconda 공식 다운로드 페이지:
https://www.anaconda.com/download/success

### 2. Conda 가상환경 생성

Python 3.10 환경을 새로 만듭니다.

```bash
conda create -n py310 python=3.10
```

### 3. 가상환경 활성화

```bash
conda activate py310
```

### 4. 실습 패키지 설치

저장소 루트 디렉터리에서 `requirements.txt` 파일을 사용해 필요한 라이브러리를 설치합니다.

```bash
pip install -r requirements.txt
```

### 5. VS Code 설치

VS Code는 필수는 아니지만 권장합니다.
노트북 실행, 코드 수정, 파일 경로 확인, 터미널 사용을 한 화면에서 처리하기 쉽습니다.

VS Code 공식 다운로드 페이지:
https://code.visualstudio.com/

VS Code에서 노트북을 실행할 때는 커널을 `py310` 가상환경으로 선택해 주세요.

## 미니 RAG 경진대회

기초 과정의 예상 산출물은 아래와 같습니다.

- LangChain 기반 RAG 파이프라인
- 자동 평가 결과
- 개선 포인트를 반영한 제출 문서

미니 RAG 경진대회는 3일차에 `미니RAG경진대회.ipynb`를 기준으로 진행합니다.
