GitHub Copilot Cheat Sheet
===

[中文版本](https://github.com/jaywcjlove/reference/blob/main/docs/github-copilot.md)

This is a quick reference guide to get started with [GitHub Copilot](https://code.visualstudio.com/docs/editor/github-copilot).  

This Cheat Sheet is translated by ChatGPT. Maybe something is wrong. If you find any problems, please submit an issue.

1.Preparation
----

### 1. Account Registration

> You need to have a GitHub account and subscribe to Copilot.

Item | Description
:-|-
GitHub Account | [Registration Link](https://github.com/signup)
Subscribe to GitHub Copilot | [Subscription Link](https://github.com/features/copilot)

### 2. Install Vscode Extension
<!--rehype:wrap-class=col-span-1 row-span-1-->

> Search and install the following extensions in the extension marketplace.

Extension Name | Functionality
:-|-
`GitHub Copilot`|Code completion suggestions in the editor
`GitHub Copilot Chat`|Plugin bar for conversing with Copilot

### 3. Sign in to GitHub Account in Vscode
<!--rehype:wrap-class=col-span-1 row-span-1-->

- After installation, click on the `GitHub Copilot` plugin icon in the bottom right corner and click `Sign in to GitHub` to log in.
- Alternatively, click on the `Accounts` icon in the toolbar and click `Sign in with GitHub to use GitHub Copilot` to log in.

### 4. Copilot Subscription Plans
<!--rehype:wrap-class=col-span-2 row-span-1-->
Plan | Price | Features
:-|-|-
Copilot Individual | $10/person/month <br> (Free for students, teachers, and open-source contributors) | Code completion, Chatbot
Copilot Business| $19/person/month | Code completion, Chatbot, Command-line tool, Security vulnerability screening, Code references, Public code screening, Intellectual property, Enterprise security and privacy protection
Copilot Enterprise| $39/person/month | Business features + Personalized chat for private code repositories + Document search summaries + Git Pull Request summaries + Code review + Model fine-tuning
<!--rehype:className=show-header left-align-->

### 5. Copilot Usage Entry Points
<!--rehype:wrap-class=col-span-1 row-span-1-->
|Name | Description |
|-|-|
Inline Suggestions| Show suggestions next to the cursor in the editor
Completions Panel| Display a complete list of suggestions in the editor
Inline Chat| Initiate a conversation next to the cursor in the editor
Editor Chat| Open a full conversation interface in the editor
Slide Chat| Open a conversation interface in the sidebar of the editor
Quick Chat| Invoke the conversation interface at the top

2.Tips for Suggestions
----

### The Art of Suggestions
<!--rehype:wrap-class=col-span-1 row-span-1-->

> The relationship between you and `copilot` is like that of a writer and an illustrator.  
> You need to describe your story (i.e., `context`) as comprehensively, concisely, and clearly as possible.  
> `Copilot` will then generate beautiful illustrations (i.e., `code`) based on your story.  

### Tips for Suggestions
<!--rehype:wrap-class=col-span-1 row-span-1-->

- 1⃣️ Provide context information
- 2⃣️ Context can be predicted

### Practical Tutorials

- [Youtube GitHub Copilot Series](https://www.youtube.com/playlist?list=PLj6YeMhvp2S5_hvBl2SE-7YCHYlLQ0bPt)
- [Pragmatic techniques to get the most out of GitHub Copilot](https://www.youtube.com/watch?v=CwAzIpc4AnA)
- [How I used GitHub Copilot to build a browser extension](https://github.blog/2023-05-12-how-i-used-github-copilot-to-build-a-browser-extension/)

### Types of Context Information
<!--rehype:wrap-class=col-span-2 row-span-1-->

Type|Description
-|-
File|Copilot will analyze the currently open file and adjacent files in the editor.
Comments|Copilot will provide help and suggestions based on adjacent comments, such as docstrings, block comments, and line comments.
Naming|Good naming helps Copilot better understand your code, such as function names, variable names, and file names.
Code|Copilot will analyze your code and the surrounding code to generate helpful suggestions.
<!--rehype:className=show-header left-align-->

### Context: File

> Copilot will analyze the currently open file and adjacent files in the editor to provide appropriate suggestions based on the context.

---

> - 1. Avoid opening too many files so that Copilot can better understand your code.
> - 2. Open files that are relevant and have common characteristics.
> - 3. For new projects, you can open some template code, data files, and reference documents as example files. This will help Copilot better understand your expectations. Once you have developed some code, you can delete these example files.

### Context: Comment: Top-level comment

When creating a new file, add comments at the top of the file to describe your requirements. This is helpful for Copilot.

\* The following explanations will use `...` to indicate where Copilot starts generating.

```python
# Download file from an URL and analyze its content
# Details: 
# * Download the file from an URL
# * Save the downloaded files into `./download` folder
# * Use `filetype` of the file to specify how to parse
# * Filetype can be `.pdf`, `.html`, `.epub`, `.md` and `.txt`
# * Use NLP or OCR to get the file content
# * Tokenize the file content and get the statistics result

import  ...
```

### Context: Comment: Inline Comment

Add comments above each function or important code block to help Copilot understand some intentions or issues in your code.

\* The following instructions will use `...` to indicate where Copilot starts generating.

Add comments above the function

```python
# parse the JSON string into User object
def ...
```

---

Add comments to the code

```python
# ...
api_sever = FastApi(...)

# starting the API Sever, enable ssl, bind to 8443 port
...
```

### Context: Comment: Docstring
<!--rehype:wrap-class=col-span-1 row-span-2-->
Sometimes, when you already have a detailed design document but haven't written the functional code, you can directly use the description in the docstring to let Copilot generate the code.

```python
def send_email(to_address: Email, subject: str, content: HTML): -> StatusCode:
    """
    Send email to specified address

    Parameters
    ----------
    to_address : Email
        The email address to send to
    subject : str
        The email subject
    content : HTML
        The email content

    Returns
    -------
    StatusCode
        The sending result
    """

    ...
```

### Context: Comment: Asking questions

> If you don't want to switch to Copilot chat, comments can also be used to ask questions.

```python
# Q: What is the difference between `os.path.join` and `pathlib.PurePath`?
# A: ...
```

### Context: Comment: Todo

> You can also let Copilot generate a `todo` list for you to assess the workload.

```python
# Parse the json file into a Talks object
# TODO:
# -[ ] 1. ...
```

### Context: Naming

> Your naming should be clear enough for Copilot to understand your intent.

#### bad case

```python
a = 60

def send(dict):
    ...

class data:
    ...
```

#### good case

```python
timeout = 60

def send_email(to_address: Email, subject: str, content: HTML): -> StatusCode:
    ...

class Email:
    ...
```

### Context: Code: Code examples

> Provide code snippets to help Copilot start new development tasks better.
>
> - Frameworks and libraries used
> - Code style
> - Algorithm logic

```python
from typing import List
from typing import Optional
from sqlalchemy import ForeignKey
from sqlalchemy import String
from sqlalchemy.orm import DeclarativeBase
from sqlalchemy.orm import Mapped
from sqlalchemy.orm import mapped_column
from sqlalchemy.orm import relationship

class Base(DeclarativeBase):
    pass

class User(Base):
    __tablename__ = "user_account"
    id: Mapped[int] = mapped_column(primary_key=True)
    name: Mapped[str] = mapped_column(String(30))
    fullname: Mapped[Optional[str]]
    addresses: Mapped[List["Address"]] = relationship(
        back_populates="user", cascade="all, delete-orphan"
    )
    def __repr__(self) -> str:
        return f"User(id={self.id!r}, name={self.name!r}, fullname={self.fullname!r})"

# Email Address
...
```

### Context: Code: Data examples

> Provide data snippets to help Copilot start new development tasks better.
>
> - Data structures and types
> - Naming
> - Value processing logic

```python

dailogs = [
    {
        "timestamp": "May 1, 2023 11:00:00",
        "text": "Hello, World!",
        "speaker": "Jack",
    },
    {
        "timestamp": "May 1, 2023 11:01:00",
        "text": "Hello, Copilot!",
        "speaker": "Copilot",
    },
]

# Parse the json object into `Dialog` object
...
```

3.Shortcuts
----
<!--rehype:body-class=cols-2-->

For Mac users, it is recommended to modify shortcuts related to the alt key, as the alt key with letters on Mac may be used by the input method. If you have customized the input method `keylayout`, ignore this sentence.

In addition, for commands without shortcuts, you can invoke the `Command Palette` and execute them by entering the query keyword after filtering.

### Github Copilot
<!--rehype:wrap-class=col-span-2 row-span-1-->

#### Copilot Inline Suggestions related commands

| Command | Description | Shortcut | Mac Shortcut |
|-|:-|:-|:-|
`editor.action.inlineSuggest.trigger`| Trigger inline suggestions | `alt+\` | `alt+\`
`editor.action.inlineSuggest.showPrevious`| Show previous inline suggestion | `alt+[`| `alt+[`
`editor.action.inlineSuggest.showNext`| Show next inline suggestion | `alt+]`| `alt+]`
`editor.action.inlineSuggest.acceptNextWord`| Accept the next word of the inline suggestion | `ctl+right`| `cmd+right`
`editor.action.inlineSuggest.commit`| Accept the inline suggestion | `Tab`| `Tab`
`editor.action.inlineSuggest.hide`| Hide the inline suggestion | `Esc`| `Esc`
`editor.action.inlineSuggest.acceptNextLine`| Accept the next line of the inline suggestion | - | -
<!--rehype:className=show-header wrap-text left-align-->

#### Copilot Completions Panel related commands

| Command | Description | Shortcut | Mac Shortcut |
|-|:-|:-|:-|
`github.copilot.generate`| Open `Completions Panel` | `ctrl+enter`| `ctrl+enter`
`github.copilot.acceptCursorPanelSolution`| Accept the suggestion at the cursor in `Completions Panel` | `ctrl+/` | `ctrl+/`
`github.copilot.previousPanelSolution`| View the previous suggestion | `alt+[`| `alt+[`
`github.copilot.nextPanelSolution`| View the next suggestion | `alt+]`| `alt+]`
<!--rehype:className=show-header wrap-text left-align-->

#### Other commands in Copilot

| Command | Description | Shortcut | Mac Shortcut |
|-|:-|:-|:-|
`github.copilot.toggleCopilot`| Enable/Disable Copilot completion suggestions | -| -
`github.copilot.collectDiagnostics`| Collect diagnostics information | -| -
`github.copilot.openLogs`| Open the log window | -| -
`github.copilot.sendFeedback`| Open the community website | -| -
`github.copilot.signIn`| Sign in | -| -
<!--rehype:className=show-header wrap-text left-align-->

### Github Copilot Chat
<!--rehype:wrap-class=col-span-2 row-span-1-->

#### Copilot Chat Chat related commands

| Command | Description | Shortcut | Mac Shortcut |
|-|:-|:-|:-|
`github.copilot.interactiveEditor.explain`| Explain (selected content or the file where the cursor is) | -| -
`github.copilot.terminal.explainTerminalSelection`| Explain this (need to be used in the terminal) |-|-
`github.copilot.terminal.explainTerminalSelectionContextMenu`| Copilot: Explain this (need to be used in the terminal) | Right-click menu | Right-click menu
`github.copilot.terminal.explainTerminalLastCommand`| Explain the last command in the terminal (need to be used in the terminal) |-|-
<!--rehype:className=show-header wrap-text left-align-->

#### Copilot Chat Inline Chat related commands

| Command | Description | Shortcut | Mac Shortcut |
|-|:-|:-|:-|
`inlineChat.start`| Code inline chat | - | -
`github.copilot.interactiveEditor.generate`| Generate here (invoke the `/generate` function of inline chat at the cursor position) | - | -
`github.copilot.interactiveEditor.generateDocs`| Generate documentation | - | -
`github.copilot.interactiveEditor.generateTests`| Generate tests | - | -
`github.copilot.interactiveEditor.fix`| Fix this | - | -
<!--rehype:className=show-header wrap-text left-align-->

#### Copilot Chat Quick Chat related commands

| Command | Description | Shortcut | Mac Shortcut |
|-|:-|:-|:-|
`workbench.action.quickchat.toggle`| Enable/Disable Quick Chat | `shift+cmd+i`| `shift+cmd+i`
`github.copilot.terminal.suggestCommand`| Suggest terminal commands | `ctrl+i` (only works in the terminal) | `cmd+i`
<!--rehype:className=show-header wrap-text left-align-->

#### Copilot Chat Editor Chat related commands

| Command | Description | Shortcut | Mac Shortcut |
|-|:-|:-|:-|
`workbench.action.openChat.copilot`| Open editor chat |-|-
<!--rehype:className=show-header wrap-text left-align-->

#### Other commands in Copilot Chat

| Command | Description | Shortcut | Mac Shortcut |
|-|:-|:-|:-|
`github.copilot.interactiveSession.feedback`| Open github Issues |-|-
`github.copilot.debug.workbenchState`| Log workbench state |-|-
`github.copilot.ghpr.applySuggestion`| Provide code suggestions for Github Pull Request |-|-
<!--rehype:className=show-header wrap-text left-align-->

4.Slash Commands tips in Copilot Chat
----

> In the chat dialog, you can interact with Copilot Chat using commands starting with `/`.

### Slash Commands Example
<!--rehype:wrap-class=col-span-1 row-span-1-->

#### Slash Commands consist of four parts

|Element|Description|
|-|-|
|- Agent |    Specify the Agent, symbol is `@`, optional
|- Commands | Specify the command, symbol is `/`, optional
|- Variables |      Reference content, symbol is `#`, optional
|- User input command |     optional

#### Example

```
/explain def helloworld():...

@vscode /api 请解释 inlineChat.start 的作用

@workspace /explain def helloworld():...

在每一行代码末尾添加注释进行解释
```

#### Agent

| Agent   |Description |
|-        |:-|
@vscode   |vscode commands and plugin related questions
@workspace|Project workspace related questions

### Inline Chat Slash Commands
<!--rehype:wrap-class=col-span-1 row-span-1-->

---

> Trigger `inline chat` using the command `inlineChat.start` and then use

|Command      |Description |
|-           |:-|
/doc         |Add documentation comments here
/explain     |Explain the selected code
/fix         |Fix the selected code
/tests       |Generate unit tests for the selected code

---

> Trigger using the command `github.copilot.interactiveEditor.generate`

|Command     |Description |
|-           |:-|
/generate    |Generate here, this command cannot be entered by the user

---

> Alternatively, you can directly select the area and then enter the command in the inline chat to perform the command operation on the selected area.

|Common commands|
| - |
|Add comments at the end of each line of code for explanation|
|Make the code comply with PEP484 requirements|
<!--rehype:className=show-header wrap-text left-align-->

### Slide Chat Slash Commands
<!--rehype:wrap-class=col-span-1 row-span-2-->

> Trigger `chat` using the command `workbench.action.chat.openInSidebar` and then use  
> Or click the Copilot chat button on the sidebar  
> The Agent (environment) can also be specified in the Chat input box

#### Slash Commands

|Command         |Description |
|-           |:-|
/api         |Answer questions about vscode extension plugin development  
/explain     |Explain the selected code
/fix         |Fix the selected code
/new         |Create a new project workspace
/newNotebook |Create a new Jupyter Notebook  
/terminal    |Explain the commands in the command line
/tests       |Generate unit tests for the selected code
/help        |Help instructions
/clear       |Clear the session

### `/terminal` specific variables, starting with `#`

> Only available in the `/terminal` command

| Variable |Description |
|-|:-|
`#terminalLastCommand`|The last executed terminal command
`#terminalSelection`|The selected terminal command

### Slash Commands in Quick Chat and Editor Chat

- Quick Chat and Chat have the same Slash Commands
- Editor Chat and Chat have the same Slash Commands

5.Parameter Settings
----

Open the VS Code command palette and enter `Preferences: Open Settings` to open the configuration file. Configure the relevant parameters in file mode.

You can find the complete parameter description in the `package.json` files of the `copilot` and `copilot chat` plugins in the [extension marketplace](https://code.visualstudio.com/docs/editor/extension-marketplace#_where-are-extensions-installed).

### Complete Configuration Reference

```json
// settings.json
{   
    // ...
    "github.copilot.chat.welcomeMessage": "always",
    "github.copilot.chat.localeOverride": "auto",
    "github.copilot.editor.enableCodeActions": true,
    "github.copilot.editor.iterativeFixing": true,
    "github.copilot.editor.enableAutoCompletions": true,
    "github.copilot.enable": {
        "plaintext": false,
        "ini": false,
        "markdown": true,
        "*": true
    },
    "github.copilot.advanced": {
        "length": 4000,
        "inlineSuggestCount": 5,
        "top_p": 1,
        "temperature": "0.8",
        "listCount": 10,
        "stops": {
            "python": [
                "\ndef ",
                "\nclass ",
                "\nif ",
                "\n\n#"
            ],
            "*": [
                "\n\n\n"
            ]
        },
        "debug.showScores": true,
        "indentationMode": {
            "python": false,
            "javascript": false,
            "javascriptreact": false,
            "jsx": false,
            "typescript": false,
            "typescriptreact": false,
            "go": false,
            "ruby": false,
            "*": true
        }
    }
    // ...
}
```

### Parameter Description
<!--rehype:wrap-class=col-span-2 row-span-1-->
#### Proxy Parameters

|Setting |Value Type|Description |
|:--|:--|:--|
`"http.proxy"`| string |Configure the network proxy address

#### Copilot Chat Parameters

|Setting |Value Type|Description |
|:--|:--|:--|
`"github.copilot.chat.localeOverride"`| string | Set the Copilot language
`"github.copilot.chat.welcomeMessage"`| string |Whether to display a welcome message in Copilot Chat<br>`first`: only on the first launch, `always`: always, `never`: never

#### Copilot Basic Parameters

|Setting |Value Type|Description |
|:--|:--|:--|
`"editor.inlineSuggest.enabled"`| boolean |Enable inline suggestions
`"github.copilot.editor.iterativeFixing"`| boolean| Allow Copilot to provide iterative fixing suggestions
`"github.copilot.editor.enableAutoCompletions"`| boolean |Allow Copilot to provide auto completions
`"github.copilot.editor.enableCodeActions"`| boolean| Allow Copilot to provide code actions, which may include code refactoring, optimizing code structure, fixing errors, etc.

#### Setting File Types for Copilot

|Setting |Value Type|Description |
|:--|:--|:--|
`"github.copilot.enable"`| json |Please put `"*": true` at the end. <br> other [language](https://code.visualstudio.com/docs/languages/identifiers) to disable Copilot, set `false` to disable, set `true` to enable

#### Copilot Advanced Parameters

> github.copilot.advanced controls model parameters, which ultimately affect code generation. Its value is json.

|Setting |Value Type|Description |
|:--|:--|:--|
`"length"`| integer | Number of code words generated, default is `500`
`"top_p"`| number | Control the range of model candidates, default value is `1`, value range is `0.0~1.0`
`"temperature"`| string | Control the creativity of the model, default value is `""`, the larger the value, the more unpredictable, value range is `0.0~1.0`
`"inlineSuggestCount"`| integer | Number of inline suggestions, default is `3`
`"listCount"`| integer | Control the number of suggestions in the `Completions Panel`, default is `10`
`"stops"`| json | Control the stop signs when generating model code, can be controlled by [language](https://code.visualstudio.com/docs/languages/identifiers)
`"indentationMode"`| json | Specify whether the [language](https://code.visualstudio.com/docs/languages/identifiers) adopts the indentation mode of that language, which may conflict with stops. For example, when using `\{\}` for indentation, comprehensive consideration is needed when setting this parameter.
`"debug.showScores"`| boolean | Show the score of each suggestion in the code suggestion list
<!--rehype:className=wrap-text -->

END... ENJOY YOURSELF
----

> Welcome everyone to add new content

Reference
----

\[1\]: [GitHub Copilot in VS Code](https://code.visualstudio.com/docs/editor/github-copilot)  
\[2\]: [How to use GitHub Copilot: Prompts, tips, and use cases](https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/)  
\[3\]: [GitHub Copilot Official Website](https://github.com/features/copilot)  
\[4\]: [GitHub Copilot Series (Youtube)](https://www.youtube.com/playlist?list=PLj6YeMhvp2S5_hvBl2SE-7YCHYlLQ0bPt)  
\[5\]: [Pragmatic techniques to get the most out of GitHub Copilot  (Youtube)](https://www.youtube.com/watch?v=CwAzIpc4AnA)  
\[6\]: [How I used GitHub Copilot to build a browser extension](https://github.blog/2023-05-12-how-i-used-github-copilot-to-build-a-browser-extension)  
\[7\]: [Visual Studio Code, Where are extensions installed?](https://code.visualstudio.com/docs/editor/extension-marketplace#_where-are-extensions-installed)  
\[8\]: [Visual Studio Code, Language Identifiers](https://code.visualstudio.com/docs/languages/identifiers)  
