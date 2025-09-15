```mermaid
graph TD
    A[开始] --> B{选择项目类型？}
    B -- Web项目 --> C[使用React]
    B -- 移动应用 --> D[使用Flutter]
    C --> E[完成]
    D --> E
