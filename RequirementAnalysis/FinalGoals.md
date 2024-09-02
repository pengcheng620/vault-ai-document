## Vault AI 系统的关键组件和流程

### 1. 智能体 (Agent)

**功能描述 (Functionality)**:
智能体是整个系统的核心决策者，负责接收用户的请求，将任务分配给相应的工具模块，并收集各个工具的输出，最终生成用户所需的结果。

**流程 (Workflow)**:
- 当用户发出指令时，智能体会首先解析请求，并将任务拆分为不同的子任务。
- 根据子任务的类型，智能体会调用合适的工具模块执行。例如，搜索任务交给 `search_tool`，而特定的文件操作（如图纸更新）则交给 `Items Action Tools`。
- 收集各个工具的结果，并将最终结果反馈给用户。

### 2. 搜索工具 (search_tool)

**功能描述 (Functionality)**:
负责接收用户的搜索请求，在 Vault 系统中执行文件搜索，并返回符合条件的文件列表。

**流程 (Workflow)**:
- 智能体将用户的搜索请求传递给 `search_tool`。
- `search_tool` 在 Vault 系统中搜索文件，并将搜索结果传递回智能体。
- 这些搜索结果可能会作为后续操作的输入，例如图纸更新。

### 3. 项目操作工具 (Items Action Tools)

**功能描述 (Functionality)**:
负责执行特定的文件操作，如图纸更新、获取缩略图等。该工具接收来自 `search_tool` 的输入并执行相应的操作。

**流程 (Workflow)**:
- 智能体将执行类型（如更新图纸）和搜索结果传递给 `Items Action Tools`。
- `Items Action Tools` 执行请求的操作，并将结果返回给智能体。

### 4. 其他工具模块 (Other Tools)

**功能描述 (Functionality)**:
系统还可以包含其他特定功能的工具模块，例如通知工具、日志记录工具等，这些工具可以根据需要调用。

**流程 (Workflow)**:
- 这些工具可以在需要时被智能体调用，执行特定的辅助操作，并将结果或状态信息反馈给智能体。

### 关键流程示例 (Key Workflow Example)

- **用户请求 (User Request)**: 用户发出指令，例如“帮我搜索xx文件并更新其中xx的图纸”。
- **智能体任务分解 (Agent Task Decomposition)**: 智能体接收请求，分解为两个子任务：
  - 搜索文件 (`search_tool`)
  - 更新图纸 (`Items Action Tools`)
- **搜索工具执行 (Search Tool Execution)**: `search_tool` 执行搜索并返回搜索结果。
- **项目操作工具执行 (Items Action Tool Execution)**: `Items Action Tools` 使用搜索结果执行图纸更新。
- **结果返回 (Result Return)**: 智能体收集各工具的执行结果，并将最终结果返回给用户。

## Key Components and Workflow of Vault AI System

### 1. Agent

**Functionality**:
The agent is the core decision-maker of the system. It receives user requests, allocates tasks to appropriate tool modules, gathers outputs from these tools, and finally compiles the results to be presented to the user.

**Workflow**:
- If the user issues a command, the agent first parses the request and breaks it down into different sub-tasks.
- Depending on the type of sub-task, the agent calls the appropriate tool module to execute it. For instance, search tasks are delegated to `search_tool`, while specific file operations (like updating drawings) are handed to `Items Action Tools`.
- The agent gathers the results from each tool and feeds the final outcome back to the user.

### 2. Search Tool

**Functionality**:
This tool handles the user's search requests, performs file searches within the Vault system, and returns a list of matching files.

**Workflow**:
- The agent passes the user's search request to the `search_tool`.
- The `search_tool` performs the search within the Vault system and sends the search results back to the agent.
- These search results may serve as input for subsequent operations, such as drawing updates.

### 3. Items Action Tools

**Functionality**:
This tool is responsible for executing specific file operations like updating drawings or fetching thumbnails. It receives input from the `search_tool` and performs the corresponding actions.

**Workflow**:
- The agent passes the action type (e.g., update drawing) and search results to the `Items Action Tools`.
- The `Items Action Tools` performs the requested operation and returns the results to the agent.

### 4. Other Tools

**Functionality**:
The system may also include other tool modules for specific functions like notification tools, logging tools, etc., which can be invoked as needed.

**Workflow**:
- These tools can be invoked by the agent as needed to perform specific auxiliary operations and report back results or status information.

### Key Workflow Example

- **User Request**: The user issues a command, such as "Help me search for xx file and update xx drawing within it."
- **Agent Task Decomposition**: The agent receives the request and decomposes it into two sub-tasks:
  - Search for the file (`search_tool`)
  - Update the drawing (`Items Action Tools`)
- **Search Tool Execution**: The `search_tool` performs the search and returns the search results.
- **Items Action Tool Execution**: The `Items Action Tools` uses the search results to execute the drawing update.
- **Result Return**: The agent collects the execution results from each tool and returns the final outcome to the user.


## Requirement: Context-Based Function Call Using LangChain

### Workflow

- Retrieve the user's chat history.
- If the user's query is related to the previous chat context, invoke the corresponding function.
- Use the context function to call the search API with multiple conditions.

### Architecture Diagram

### Use Case

- User: Search for all files named "water heater".
- AIBot: Returns a table of all "water heater" files ("Water Heater.iam", "Water Heater.ipt" ...).
- User: Perform checkout on "Water Heater.iam" from the table.
- AIBot: Operation completed (API call).

### Technical Details

### Workload Estimation Based on Use Case

### Summary

### Issues

## 需求： 基于上下文的 function call 的调用（使用langchain）

- 工作流
    1. 获取用户聊天上下文的历史记录。
    2. 如果用户的问题与之前的聊天上下文相关，调用相应的函数。
    3. 提取上下文中的重要信息作为参数传递给函数，该函数调用 Vault API。

- 流程图

## Use Case 2 for AU demo – Design Task – Update all drawings

### On project P-000014, I can’t recall which 2D drawings are already up-to-date and which still require an update prior to release to production.

- **User**: Please show me all 2D drawings within project P-03453, which are out of date.
- **AIBot**: I found 10 drawings which require an update. However, 5 of them have markup and might require your
  attention while updating them. Do you want me to update those 5 drawings (a list of drawings with links is exposed in
  the results) without markup for you?
- **User**: Yes, please.
- **AIBot**: This will take some time, I believe around 2 minutes. I will let you know when it is finished.
- **AIBot**: All drawings are now up-to-date. Do you want me to kick off the release process for those drawings?
- **User**: That would be awesome.
- **AIBot**: Yes, please.


- 技术细节
    1. 上下文管理：

    - 保存对话历史记录到本地或者数据库，确保上下文的持久性和可检索性。

    2. 自然语言处理：  
       使用 OpenAI 的 API 解析用户的自然语言输入。
       将自然语言输入转换为结构化的 API 调用请求。
       API 调用：  
       根据解析结果调用相应的 Vault/Inventor API。
       处理 API 的响应并将结果返回给用户。
       用户交互：  
       提供交互式按钮，用户点击后可以执行特定操作（如 checkout 文件）。
       确保用户界面的友好性和易用性。


- 基于案例的工作量评估

### Blocks

- Langchain needs the api key of azure openai.(current we directly call with token method, we don't use langchain)

### 总结

- 在本例中使用到了 langchain
  的两个方法分别是 [Tool-Calling](https://python.langchain.com/v0.2/docs/how_to/tool_calling/) 以及 chain function call

### Use Case 1 for AU demo – Re-use instead of create another duplicate: CAD Place/ Create a new Component

#### As a Mechanical Engineer, I need to create a new component. However, I don’t know whether such a component or a similar component already exists. Can Vault assistance help me here?

- **User**: Show me the most used components with the title or description containing "Turbine impeller" and material "
  stainless steel" released no later than Jan 2023.
- **AIBot**: I found 8 components based on your criteria. 3 components are identical based on geometry duplicate search.
  The results are displayed in a table with several metadata comparisons (including Mass, Volume, and other properties
  like thumbnail). What are the components with the lowest carbon data impact (sustainability requirements)?
- **User**: 4 components comply with the requirements and have the lowest carbon data impact (2 of the 4 are identical
  based on duplicate search). I would like to have component PART-23453 placed in my assembly.
- **AIBot**: The component is now placed in your open assembly.

### Use Case 2 for AU demo – Design Task – Update all drawings

#### On project P-000014, I can’t recall which 2D drawings are already up-to-date and which still require an update prior to release to production.

- **User**: Please show me all 2D drawings within project P-03453, which are out of date.
- **AIBot**: I found 10 drawings which require an update. However, 5 of them have markup and might require your
  attention while updating them. Do you want me to update those 5 drawings (a list of drawings with links is exposed in
  the results) without markup for you?
- **User**: Yes, please.
- **AIBot**: This will take some time, I believe around 2 minutes. I will let you know when it is finished.
- **AIBot**: All drawings are now up-to-date. Do you want me to kick off the release process for those drawings?
- **User**: That would be awesome.
- **AIBot**: Yes, please.

### Use Case 3 for AU demo – Custom Order P-003456

#### As Mechanical engineer I need to create new design based on a custom order with predefined requirements (I just got a message from project manager).

- **User**: Show me recent designs for orders for Filtration Tower.
- **AIBot**: I found 8 assemblies from the past. Your colleague @medi.kota recently created the following design
  ASM-20450 and leveraged materials XXX to meet sustainability requirements (carbon footprint). However, the long lead
  time for certain components/material delayed the project delivery for a few weeks. On the other side, @max.geiger
  created the following design ASM-43678 which still complies with sustainability requirements by leveraging components
  from another supplier. It was more costly, but the project delivery was on time. Do you want me to compare the
  metadata of both designs for you?
- **User**: Yes, that would be great.
- **AIBot**: Here are the results (table with comparison of costs and other data).
- **User**: I would like to start with Max’s design as a template for the new order. Please create a new design
  ASM-50650 based on ASM-43678 where the module branch Discharge Unit and the collector housing are copied, and the rest
  of the modules are reused. Please leverage the default numbering scheme and other settings.
- **AIBot**: Based on your instructions, here is the proposed structure for the new design ASM-50650 in the copy design
  workflow. Do you want me to execute the copy?
- **User**: Yes, please.
- **AIBot**: The design is now created and managed in Vault. Do you want me to open this for you in Inventor?
- **User**: Yes, please.
