
Langgraph란?
specialized library within LangChain to build stateful multi-agent systems
process input : add task, complete task, summarize task : total of 3 nodes and connected with edges
llm을 활용한 workflow를 구현하기 위한 프레임워크
시스템의 상태 (state)를 기반으로 동작
흐름은 그래프 (node-edge)로 표현
동적 동작 제어와 관리를 통해 고도화된 agentic systems 구현


LangChain이란?
1. Retreive data            <- Document Loader / Text Spliter
2. Summarize the data       <- Chain of (prompt, LLM)
3. Answer user's prompt     <- Chain of (Memory(conversation history), prompt, LLM)
Chain structure (DAG: Directed Acyclic Graph)


1. LangChain과 LangGraph를 활용한 에이전트 시스템 구성
LangChain 주요 컴포넌트 이해 (Chains, Tools, Memory, Agents)
LangGraph를 통한 Stateful Multi-Agent System 설계

3. Memory와 상태 관리 전략
Short-term memory vs. Long-term memory
ConversationContext 유지 → 지속 대화 에이전트 구현
Vector memory + RAG 통합


#### References & 추가 자료
https://python.langchain.com/docs/introduction/  
https://www.youtube.com/watch?v=qAF1NjEVHhY  
https://www.youtube.com/watch?v=1bUy-1hGZpI&t=6s  
https://www.youtube.com/watch?v=yMalr0jiOAc    <---------  보기
