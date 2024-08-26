# Requirement Analysis Document

# Fundamental Requirement:
- Develop a sidebar plugin for Autodesk Vault that enables an AI-Bot to directly interact with the Vault client. Utilize AI to make the use of the Vault system simpler and more efficient for users.

## 1. Introduction

### 1.1 Project Background

In modern engineering design and manufacturing industries, companies rely on efficient Product Data Management (PDM) systems to organize and manage a large number of design files and documents. Autodesk Vault is a widely used PDM software that provides users with powerful version control, file management, and team collaboration features. However, as the volume of data increases, users often face tedious and repetitive tasks when operating and managing files in Vault, affecting work efficiency.

To address these challenges, this project aims to develop an integrated AI-Bot sidebar plugin for Autodesk Vault. Through this plugin, users can interact directly with the Vault system using natural language, significantly simplifying file operation processes and improving work efficiency. The AI-Bot will provide intelligent search, automated operations, personalized suggestions, and other features, enabling users to manage and operate files in Vault more easily.

By introducing AI technology, the project aims to elevate the user experience of the Vault system to a new level, helping companies maintain efficiency and competitiveness in increasingly complex design environments.

### 1.2 Project Scope

**Functional Boundaries**

- Core Features:
    - Natural Language Search: Users can input file search requests in natural language. The AI-Bot will understand and execute the search, returning results to the user.
    - Simplified File Operations: Users can directly perform file operations in Vault (such as open, Check In, Check Out, delete files, etc.) through the AI-Bot, simplifying the process.
    - Automated Workflows: The AI-Bot can trigger automated operations via commands, such as batch file operations or drawing update processes.
    - Recommendations and Tips: Based on user habits, the AI-Bot can provide personalized file recommendations and operation tips.
    - Notifications and Alerts: The AI-Bot can send real-time notifications to users based on changes in Vault files, such as file updates or approval process changes.
- Excluded Features:
    - Training and deployment of large AI language models (external dependency, can use models trained by other departments)
    - Non-Vault related functionalities

**Time Boundaries**

- Project Start Date: xx/xx/2024
- Project End Date: xx/xx/2025
- Major Milestones:
    - Completion of Requirement Analysis and Design: 31/08/2024
    - Development Completion: xx/xx/2025
    - Testing Completion: xx/xx/2025

**Resource Boundaries**

- Human Resources: The project team includes x project managers, x developers, x testers.
- Material Resources: Hardware and software equipment required for development and testing.

## 2. Overview of Requirements

### 2.1 Typical User Scenarios：

- **Quick File Search**: Users search for a design file in Vault without knowing its exact location. By inputting "find the most recently updated design file" into the AI-Bot, the search results are displayed directly.

- **Batch Operations**: Users need to transfer a batch of files from the development environment to the production environment. The AI-Bot can trigger a batch Check-In operation with a single command.

- **Automated Workflow Reminders**: Users want real-time reminders of the progress of approval processes. The AI-Bot will notify users based on the approval status of files in Vault.

### 2.2 用户需求

1. **Efficient File Search**: Users want to quickly search for files in the Vault system using natural language input and display the results in a table format.
2. **File Version Management**: Users want to manage file versions through the AI Bot, including viewing historical versions and rolling back to specific versions.
3. **Team Collaboration Features**: Users can query the current status of a project, view file approval processes, or send reminders or notifications to specific members.
4. **Contextual Operations in Vault**: Users want to be able to select text, files, or take screenshots on the Vault main page, and then use the right-click menu or shortcuts to call the AI Bot for operations.
5. **File Operations and Drawing Management**: Users want to open files directly in Vault and perform Check In/Check Out operations by clicking on the file names in the search results.
6. **Historical Conversation Records**: Users want to view and search historical conversation records with the AI Bot to find previous dialogue content.
7. **Interactive Buttons**: Users want interactive buttons in the AI Bot's responses that can execute specific operations, such as linking to external sites or performing internal Vault file operations.
8. **Personalized Recommendations**: Users want the AI Bot to provide personalized file recommendations and operation tips based on their historical actions and preferences.
9. **Voice Input**: Users want to interact with the AI Bot using voice input to improve input efficiency.

### 2.3 系统需求

1. **集成 AI 聊天机器人**: 系统需要在 Autodesk Vault 的侧边栏中集成 AI 聊天机器人，实现自然语言问答功能。
2. **文件搜索功能**: 系统需要通过自然语言理解调用 Vault/Inventor 等内部 API，实现文件搜索功能，并以表格形式展示搜索结果。
3. **文件操作功能**: 系统需要提供交互式按钮，用户点击后可以调用 API 实现 Vault 内部文件的操作，如打开文件、Check In、Check
   Out 等。
4. **图纸更新功能**: 系统需要通过自然语言理解用户需求，调用 Vault 等内部 API，实现图纸更新功能。
5. **历史对话记录**: 系统需要保存用户与 AI 聊天机器人的历史对话记录，并提供搜索功能。
6. **安全性**: 系统需要确保用户数据和操作的安全性，包括认证和授权机制。
7. **性能要求**: 系统需要在高并发情况下保持良好的性能，确保响应速度和稳定性。
8. **可用性**: 系统需要具备高可用性，确保在各种情况下都能正常运行。
9. **个性化推荐**: 系统需要根据用户的历史操作和偏好，提供个性化的文件推荐和操作提示。
10. **语音输入**: 系统需要支持语音输入功能，以提高用户输入效率。
11. **移动端支持**: 系统需要支持移动设备访问和操作 AI Bot，实现随时随地的使用。

## 3. 功能需求

### 3.1 文件搜索功能

**描述**: 用户通过自然语言输入搜索请求，系统调用 Vault/Inventor API 进行文件搜索，并以表格形式展示搜索结果。

**需求**:

- 系统应支持自然语言输入的文件搜索请求。
- 系统应调用 Vault/Inventor API 进行文件搜索。
- 系统应以表格形式展示搜索结果。
- 用户应能通过点击表格中的文件名在 Vault 中打开文件。

### 3.2 文件操作功能

**描述**: 用户通过点击搜索结果中的文件名，系统调用 API 实现 Vault 内部文件的操作，如打开文件、Check In/Check Out 等。

**需求**:

- 系统应提供交互式按钮，用户点击后调用 API 实现 Vault 内部文件的操作。
- 系统应支持文件的打开、Check In/Check Out 等操作。

### 3.3 图纸更新功能

**描述**: 用户通过自然语言输入更新图纸的请求，系统调用 Vault/Inventor API 实现图纸更新。

**需求**:

- 系统应支持自然语言输入的图纸更新请求。
- 系统应调用 Vault/Inventor API 实现图纸更新。
- 系统应提供更新图纸的按钮，用户点击后调用 API 实现图纸更新。

### 3.4 历史对话记录

**描述**: 系统保存用户与 AI 聊天机器人的历史对话记录，并提供搜索和查看功能。

**需求**:

- 系统应保存用户与 AI 聊天机器人的历史对话记录。
- 系统应提供对话记录的搜索和查看功能。

### 3.5 实时通知

**描述**: 用户在 Vault 中的文件发生变化时，系统通过 AI Bot 实时通知用户。

**需求**:

- 系统应支持文件变化的实时通知功能。
- 系统应通过 AI Bot 实时通知用户文件的变化。

## 4. 非功能需求

### 4.1 性能需求

**描述**: 系统在高并发情况下保持良好的性能，确保响应速度和稳定性。

**需求**:

- 系统应在高并发情况下保持良好的性能。
- 系统应确保响应速度和稳定性。

### 4.2 安全性需求

**描述**: 系统确保用户数据和操作的安全性，包括认证和授权机制。

**需求**:

- 系统应确保用户数据的安全性。
- 系统应提供认证和授权机制。

### 4.3 可用性需求

**描述**: 系统具备高可用性，确保在各种情况下都能正常运行。

**需求**:

- 系统应具备高可用性。
- 系统应确保在各种情况下都能正常运行。

### 4.4 多语言支持

**描述**: 系统支持多种语言，以便不同语言的用户都能使用。

**需求**:

- 系统应支持多种语言。

### 4.5 移动端支持

**描述**: 系统支持移动设备访问和操作 AI Bot，实现随时随地的使用。

**需求**:

- 系统应支持移动设备访问和操作。

## 5. 用例

### 5.1 用例 1 (Search by AI Bot)

**描述**: 通过自然语言理解调用 Vault/Inventor 等内部 API，实现文件搜索功能。通过表格形式展示搜索结果。通过点击表格内容实现在
Vault 中打开文件、Check In/Check Out 等一系列文件操作。

**参与者**:

- 主参与者: 用户
- 次参与者: AI Bot, Vault 系统

**前置条件**:

- 用户已登录 Vault 系统。
- AI Bot 已集成在 Vault 侧边栏。

**主要流程**:

1. 用户在 AI Bot 中输入搜索请求。
2. AI Bot 解析用户请求并调用 Vault/Inventor API 进行文件搜索。
3. AI Bot 将搜索结果以表格形式展示给用户。
4. 用户点击表格中的文件名。
5. AI Bot 调用 Vault API 在 Vault 中打开文件。

**替代流程**:

- 如果搜索请求无结果，AI Bot 提示用户无匹配结果。
- 如果 Vault API 调用失败，AI Bot 提示用户操作失败。

**后置条件**:

- 用户成功查看或操作了 Vault 中的文件。

### 5.2 用例 2 (Update Drawings)

**描述**: 通过自然语言理解用户需求，明确用户需要更新图纸。点击 AI Bot 中的按钮后，调用 Vault/Inventor 等内部 API，实现更新图纸的功能。

**参与者**:

- 主参与者: 用户
- 次参与者: AI Bot, Vault 系统

**前置条件**:

- 用户已登录 Vault 系统。
- AI Bot 已集成在 Vault 侧边栏。

**主要流程**:

1. 用户在 AI Bot 中输入更新图纸的请求。
2. AI Bot 解析用户请求并确认需要更新图纸。
3. AI Bot 提供更新图纸的按钮。
4. 用户点击更新图纸按钮。
5. AI Bot 调用 Vault/Inventor API 进行图纸更新。

**替代流程**:

- 如果用户请求不明确，AI Bot 提示用户重新输入请求。
- 如果 Vault API 调用失败，AI Bot 提示用户操作失败。

**后置条件**:

- 用户成功更新了 Vault 中的图纸

## 6. 数据需求

### 数据类型:

- 用户输入的自然语言请求
- Vault 系统中的文件元数据
- AI Bot 的对话记录
- API 调用的请求和响应数据

### 数据量:

- 取决于用户的使用频率和 Vault 系统中的文件数量
- 对话记录和搜索结果可能会随着时间增长，需要考虑存储和检索的效率

## 7. 接口需求

### 内部接口:

- Vault/Inventor API: 用于文件搜索、文件操作、图纸更新等功能
- AI Bot 内部接口: 用于处理自然语言请求和生成响应

### 外部接口:

- 用户界面接口: 用于与用户交互，接收用户输入和展示搜索结果
- 实时通知接口: 用于在文件发生变化时通知用户