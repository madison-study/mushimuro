 ## AI Agent 핵심 요소
- 자연어 생성 및 이해 능력을 갖춘 LLM은 시스템의 ‘두뇌’ 역할을 합니다.
- AI가 외부 세계와 통신하거나, 데이터를 얻거나, 특정 작업을 수행해야 하는 경우 '외부 리소스'나 ‘API’를 활용할 수 있습니다. 
- 신중하게 구성된 질문이나 지시는 '프롬프트'로 제공되어 LLM의 행동과 인지 과정을 지시합니다.

- 첫 번째는 'Chain-of-Thought'입니다. (이 개념은 2022년 Google Brain 논문에서 소개됨)
	- 이 논문은 LLM이 복잡한 문제를 더 작은 중간 단계로 나눈 후, 각 단계를 연속적으로 수행하여 전체 문제를 해결할 수 있는 능력이 있음을 증명함
	- 이 기법은 Agent의 핵심인 LLM의 다단계 추론 및 계획 능력을 크게 향상시킴 
	- CoT의 복잡한 문제를 해결하기 위해 LLM이 논리적이고 순차적으로 사고하도록 장려하는 기술 - Reason and Acting

- 두 번째는 인간의 직접적인 입력 없이 'tool' + 'memory'를 사용하여 여러 작업을 연속으로 수행 
	- 'tool'은 프롬프트가 제공될 때 검색되고 사용되는 정보 저장소를 나타냄
	- 'memory'는 Agent가 과거의 프롬프트와 출력을 통해 얻은 학습된 경험을 나타냄
	- tool + memory를 통해 LLM은 설정된 목표를 완료하기 위해 자율적으로 행동할 수 있는 시스템 역할을 수행함

---

## AI agent memory
<img src="./resource/memory_system.png" width="400px">

- AI 시스템의 과거 행동을 저장 및 불러오기를 하는 능력을 말함. 이를 통해 decision-making, perception, overall performance를 향상시킴
- AI agent는 memory를 통해 맥락을 유지하고, 시간이 지나면서 패턴을 인식하며, 과거 상호작용을 기반으로 적응할 수 있음
	- 예시로, 일반적인 thermostat은 단순히 현재 온도를 보고, 난방을 틀기/끄기 를 진행한다. 하지만, "smart"한 온도계는 학습된 memory를 통해 과거 및 현재의 온도를 분석하여 더 나은 의사결정을 할 수 있다.
- AI memory design's biggest challenge 중 하나는 검색 효율 최적화이다. 너무 많은 데이터를 저장하면 검색속도가 느려지기 때문에 상황에 맞는 설계가 필요

---

## Types of Agentic memory
- Short-term memory
	- remember recent inputs for immediate decision-making
	- useful in conversational AI
	- typically implemented using rolling buffer or context window (LLM이 한번에 읽을수 있는 token; LLM 자체의 임시메모리)
- Long-term memory
	- allows AI agent to store & recall across different sessions -> more personalized and intelligent over time
	- designed for permanent storage
	- implemented using db (db, graph-db, vector-db)

#### LTM types
- Episodic memory
	- operate based on past experiences and event-specific memory
	- follow a strategy of recalling previously logged actions and outcomes to inform present decisions
	- ex) AI 금융 어드바이저가 사용자의 이전 투자 이력을 기반으로 추천 제공, 자율주행 로봇이 과거 경로를 기억해 최적 경로 선택
	- pro: 적응력이 뛰어나며, 과거 실패를 반복하지 않고 학습된 사례 기반으로 더 나은 의사결정 가능
	- con: 이벤트 로그가 방대해지면 검색 효율성 문제 발생, 설계와 유지에 높은 비용 요구
  
- Semantic memory
	- operate based on generalized factual knowledge rather than specific experiences
 	- follow rules, ontologies, 또는 임베딩 기반의 지식 구조를 통해 논리적 추론 수행
  - ex) 법률 AI가 판례 데이터베이스를 통해 조언, 의료 진단 도구가 의학 지식을 활용
  - pro: 체계적이고 일관된 판단 가능, 전문가 시스템에 적합
  - con: 맥락 반영이나 사건 기반 유연성 부족, 업데이트 어려움
    
- Procedural memory
	- operate based on learned sequences of actions or skills
	- follow 자동화된 행동 패턴이나 행동 정책(policy)을 통해 별도 추론 없이 작업 수행
	- ex) 로봇이 학습된 조립 동작 수행, AI가 반복 작업을 효율적으로 자동화
	- pro: 고속, 저비용 작업 수행 가능. 반복적 작업에서 효율성 극대화
	- con: 상황 변화에 유연하게 대응하기 어려움. 잘못된 행동을 학습하면 계속 반복될 수 있음

---

# Types of AI Agent
- Simple reflex agent
	- operate based on direct responses to environmental conditions
	- follow predefined rules (aka condition-action rules) to make decisions without considering past experiences or future consequences.
	- ex) thermostat, automatic traffic light system
	- pro : effective in structured and predictable env
	- con : 복잡한 scenario에서 작동 어려움. 같은 실수를 반복적이로 할 수 있음
- Model-based reflex agent
	- operate based on condition-action rules + 내부 환경 모델
	- follow 현재 상태와 과거 상호작용 정보를 함께 고려하여 행동 결정
	- ex) 로봇이 장애물을 피할 때, 이전 경로와 장애물 위치까지 기억하여 더 똑똑하게 이동
	- pro: 부분적으로 관측 가능한 환경에서도 잘 작동, 과거 상태를 추적하여 더 나은 판단 가능
	- con: 여전히 학습 기능은 없으며, 복잡한 환경에 대한 고급 추론은 어려움
- Goal-based agent
	- operate based on 목표 지향적 의사결정 + 계획(Planning) 기능
	- follow 정해진 목표에 도달하기 위한 최적의 행동 경로를 선택
	- ex) 특정 방에 도달하기 위해 경로를 계획하는 자율주행 로봇
	- pro: 미래 상태까지 고려한 결정을 내릴 수 있어 유연성과 목표 달성 능력 향상
	- con: 목표 설정 및 평가 전략이 고정되어 있거나 제한적일 수 있음, 적응력은 제한적
- Utility-based agent
	- operate based on 다양한 선택지의 효용(utility)을 비교하여 최적 선택
	- follow 목표 달성뿐 아니라 여러 요소 간의 trade-off를 고려한 판단 수행
	- ex) 자율주행차가 빠른 경로, 연료 효율성, 안전성 간의 균형을 계산해 최적의 경로 선택
	- pro: 복잡한 환경에서 다중 목표를 동시에 고려해 더욱 똑똑한 행동 가능
	- con: 효용 함수를 정확히 정의하고 조정하는 것이 어렵고 비용이 많이 듬
- Learning agent
	- operate based on 환경과의 상호작용을 통해 경험적으로 성능 개선
	- follow 피드백 기반 학습 구조 (Performance, Learning, Critic, Problem Generator 등)
	- ex) 강화학습 기반 에이전트가 보상 신호를 통해 전략을 개선해가는 구조 (예: 자율주행, 게임 AI)
	- pro: 복잡하고 예측 불가능한 환경에서 스스로 적응 및 개선 가능
	- con: 충분한 학습 데이터 및 시간이 필요하며, 학습이 잘못되면 성능 저하 가능

---

# Multi agent
<img src="./resource/multi_agent.png" width="400px">

- Divide and Conquer
  
**VS Code에서 실습**

---

# Reference
https://www.samsungsds.com/kr/insights/integrating-ai-assistants-into-business-workflows-part1.html  
https://www.ibm.com/think/topics/ai-agent-memory  
https://www.ibm.com/think/topics/ai-agent-types  
https://langchain-ai.github.io/langgraph/tutorials/get-started/3-add-memory/#5-inspect-the-state  
https://langchain-ai.github.io/langgraph/tutorials/get-started/3-add-memory/  
https://python.langchain.com/v0.1/docs/modules/memory/  
https://arxiv.org/abs/2201.11903  

