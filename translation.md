```mermaid
raph TD
    %% 定义系统处理流程
    subgraph 系统处理流程
        A[Partner Home dev raises Static requests] --> B(CT - Continuous translator)
        B --> C(i18n Platform)
        C --> D(TP - Translations platform)
        D --> E[Translator process]
    end

    %% 定义各系统模块的职责
    subgraph CT Continuous translator
        direction TB
        B1[Receive clients requests]
        B2[Fetches PO files from client’s repository]
        B3[aintain basic mapping of  client to target locale]
    end

    subgraph i18n Platform
        direction TB
        C1[get request and send responses to clents]
        C2[Manage integrations with translators]
        C3[Uses workflow ID to execute  granular steps]
        C4[Push data for analytics and reporting]
    end

    subgraph TP Translations platform
        direction TB
        D1[Manage integrations with translators]
        D2[send request X to googleML or SmartL]
    end

    %% 定义人工翻译工作流
    subgraph Translator Process
        direction LR
        E1[Google ML --> E2[freelancer review and edit]
        E2 --> E3[Internal QA]
    end

    %% 关联主线和子图
    B --> B1 & B2 & B3
    C --> C1 & C2 & C3 & C4
    D --> D1 & D2

    E --> E1
