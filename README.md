# LangGraph - Hướng Dẫn Từ Cơ Bản Đến Nâng Cao

## 📚 Giới Thiệu

**LangGraph** là một thư viện mạnh mẽ được xây dựng trên nền tảng LangChain, cho phép bạn xây dựng các ứng dụng AI với kiến trúc dạng graph (đồ thị). Thay vì viết code tuần tự, LangGraph giúp bạn mô hình hóa logic phức tạp thành các nodes (nút) và edges (cạnh), tạo ra các workflow linh hoạt và dễ quản lý.

## 🎯 Tại Sao Sử Dụng LangGraph?

- **Kiến trúc Graph**: Mô hình hóa logic phức tạp thành các nodes và edges
- **State Management**: Quản lý state (trạng thái) một cách có cấu trúc và rõ ràng
- **Conditional Routing**: Điều hướng có điều kiện dựa trên state
- **Multi-Step Reasoning**: Xử lý các quy trình nhiều bước một cách tự nhiên
- **Dễ Debug**: Dễ dàng theo dõi và debug flow của ứng dụng
- **Tái Sử Dụng**: Các nodes có thể được tái sử dụng trong nhiều graph khác nhau

## 🔑 Các Khái Niệm Cơ Bản

### 1. State (Trạng Thái)

State là một dictionary (TypedDict) chứa tất cả dữ liệu được truyền qua các nodes trong graph. Mỗi node có thể đọc và cập nhật state.

```python
class AgentState(TypedDict):
    name: str
    age: str
    skills: List[str]
    result: str
```

### 2. Node (Nút)

Node là một function nhận state làm input và trả về state đã được cập nhật. Mỗi node thực hiện một tác vụ cụ thể.

```python
def greetingNode(state: AgentState) -> AgentState:
    state['result'] = "Hello " + state['name']
    return state
```

### 3. Edge (Cạnh)

Edge định nghĩa luồng điều khiển giữa các nodes. Có 2 loại:
- **Fixed Edge**: Luôn đi theo một hướng cố định
- **Conditional Edge**: Điều hướng dựa trên điều kiện

### 4. Graph (Đồ Thị)

Graph là tập hợp các nodes và edges, được compile thành một ứng dụng có thể chạy được.

## 📖 Nội Dung Các File Notebook

### 1. Your First LangGraph Example — Turning Logic into Flow

**File**: `1.Your First LangGraph Example — Turning Logic into Flow.ipynb`

**Mô tả**: Ví dụ đầu tiên và đơn giản nhất về LangGraph. File này giới thiệu cách tạo một graph cơ bản với một node duy nhất.

**Khái niệm học được**:
- Cách định nghĩa State với TypedDict
- Tạo StateGraph
- Thêm node vào graph
- Kết nối START và END với nodes
- Compile và sử dụng graph

**Cấu trúc Graph**:
```
START → greetingNode → END
```

**Ví dụ sử dụng**:
```python
graph = StateGraph(MsgState)
graph.add_node('init', greetingMode)
graph.add_edge(START, 'init')
graph.add_edge('init', END)
bot = graph.compile()
```

---

### 2. Structured States & Multi-Step Reasoning Explained

**File**: `2.Structured States & Multi-Step Reasoning Explained.ipynb`

**Mô tả**: Học cách xây dựng graph với nhiều nodes tuần tự, mỗi node xử lý một phần của logic và truyền state cho node tiếp theo.

**Khái niệm học được**:
- Xây dựng graph với nhiều nodes
- State được truyền qua các nodes tuần tự
- Mỗi node có thể đọc và cập nhật state
- Multi-step processing (xử lý nhiều bước)

**Cấu trúc Graph**:
```
START → firstNode → secondNode → thirdNode → END
```

**Flow xử lý**:
1. `firstNode`: Tạo lời chào với tên
2. `secondNode`: Thêm thông tin về skills
3. `thirdNode`: Thêm thông tin về tuổi

**Ví dụ sử dụng**:
```python
employee = {
    "name": "dungbt",
    "skills": ["python", "php", "AI", "Air Blade"],
    "age": "39"
}
result = bot.invoke(employee)
```

---

### 3. Conditional Routing in LangGraph

**File**: `3.Conditional Routing in LangGraph.ipynb`

**Mô tả**: Học cách sử dụng conditional routing để điều hướng flow dựa trên điều kiện trong state. Đây là một tính năng mạnh mẽ cho phép graph quyết định đường đi tiếp theo.

**Khái niệm học được**:
- Conditional edges với `add_conditional_edges()`
- Routing function để quyết định đường đi
- Xử lý nhiều nhánh logic khác nhau
- Dynamic flow control

**Cấu trúc Graph**:
```
START → router → [conditional] → adder → END
                      ↓
                 subtractor → END
```

**Flow xử lý**:
1. `router`: Node trung gian để kiểm tra điều kiện
2. `decide_next_operation()`: Function quyết định điều hướng
3. Nếu `operation == 'add'` → đi đến `adder`
4. Nếu `operation == 'subtract'` → đi đến `subtractor`

**Ví dụ sử dụng**:
```python
input_state = {
    'number_one': 10,
    'number_two': 5,
    'operation': 'add',  # hoặc 'subtract'
    'result': None
}
response = bot.invoke(input_state)
```

---

### 4. Conditional Routing in LangGraph (Duplicate)

**File**: `4.Conditional Routing in LangGraph.ipynb`

**Lưu ý**: File này có nội dung tương tự file số 3. Có thể là bản duplicate hoặc phiên bản cải tiến.

---

### 5. Multi-Branch Decision Flows Explained

**File**: `5.Multi-Branch Decision Flows Explained.ipynb`

**Mô tả**: Ví dụ nâng cao nhất, thể hiện cách xây dựng graph phức tạp với nhiều conditional routing và nhiều nhánh xử lý. Đây là pattern thường gặp trong các ứng dụng thực tế.

**Khái niệm học được**:
- Nhiều conditional routing trong cùng một graph
- Xử lý tuần tự với routing ở giữa
- Kết hợp fixed edges và conditional edges
- Complex workflow design

**Cấu trúc Graph**:
```
START → router → [conditional] → adder ──┐
                      ↓                  │
                 subtractor ─────────────┼──→ router_2 → [conditional] → add_to_four → END
                                                          ↓
                                                    subtract_from_four → END
```

**Flow xử lý**:
1. **Bước 1 - Router đầu tiên**:
   - Kiểm tra `operation`
   - Nếu `'add'` → `adder` (number_one + number_two → number_three)
   - Nếu `'subtract'` → `subtractor` (number_one - number_two → number_three)

2. **Bước 2 - Router thứ hai**:
   - Cả `adder` và `subtractor` đều đi đến `router_2`
   - Kiểm tra `operation_four`
   - Nếu `'add'` → `add_to_four` (number_three + number_four → result)
   - Nếu `'subtract'` → `subtract_from_four` (number_three - number_four → result)

**Ví dụ sử dụng**:
```python
input = {
    'number_one': 1,
    'number_two': 2,
    'number_three': 0,
    'number_four': 3,
    'operation': 'add',        # Bước 1: cộng hoặc trừ
    'operation_four': 'add'     # Bước 2: cộng hoặc trừ
}
response = bot.invoke(input)
# Kết quả: (1 + 2) + 3 = 6
```

## 🚀 Cài Đặt

```bash
pip install langgraph
```

## 📝 Cấu Trúc Code Cơ Bản

### 1. Import thư viện
```python
from typing import TypedDict
from langgraph.graph import StateGraph, START, END
```

### 2. Định nghĩa State
```python
class AgentState(TypedDict):
    field1: str
    field2: int
    result: str
```

### 3. Tạo các Node functions
```python
def myNode(state: AgentState) -> AgentState:
    # Xử lý logic
    state['result'] = "processed"
    return state
```

### 4. Xây dựng Graph
```python
graph = StateGraph(AgentState)
graph.add_node('node_name', myNode)
graph.add_edge(START, 'node_name')
graph.add_edge('node_name', END)
```

### 5. Compile và sử dụng
```python
bot = graph.compile()
result = bot.invoke(initial_state)
```

## 🎓 Lộ Trình Học

1. **Bắt đầu**: File 1 - Hiểu cách tạo graph đơn giản nhất
2. **Nâng cao**: File 2 - Học về multi-step processing
3. **Điều kiện**: File 3 - Làm quen với conditional routing
4. **Thực hành**: File 5 - Xây dựng graph phức tạp với nhiều nhánh

## 💡 Best Practices

1. **Đặt tên rõ ràng**: Đặt tên nodes và state fields một cách mô tả
2. **Tách biệt logic**: Mỗi node nên có một trách nhiệm cụ thể
3. **Type hints**: Luôn sử dụng TypedDict cho state để có type safety
4. **Documentation**: Thêm docstring cho các node functions
5. **Error handling**: Xử lý lỗi trong các nodes khi cần thiết

## 🔗 Tài Liệu Tham Khảo

- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [LangChain Documentation](https://python.langchain.com/)
- [GitHub Repository](https://github.com/langchain-ai/langgraph)

## 📄 License

MIT License

---

**Tác giả**: dungbt  
**Ngày tạo**: 2024  
**Mục đích**: Học tập và nghiên cứu về LangGraph

