---
title: 啟用 tab 鍵自動完成
description: 本文描述如何為適用於 PowerShell、Bash 和 zsh 的 .NET Core CLI 啟用 tab 鍵自動完成。
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: c7673d95f3710d78d3a09b26f031396587f9c669
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202496"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a>如何為 .NET Core CLI 啟用 TAB 鍵自動完成

從 .NET Core 2.0 SDK 開始，.NET Core CLI 支援 tab 鍵自動完成。 本文描述如何為 PowerShell、Bash 和 zsh 等三種殼層設定 tab 鍵自動完成。 其他殼層可能支援自動完成。 請參閱其文件以了解如何設定自動完成，其中的步驟應該會類似於本文中所述的步驟。

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

設定後，只要在殼層中輸入 `dotnet` 命令，然後按 TAB 鍵，即會觸發 .NET Core CLI 的 Tab 鍵自動完成。 目前的命令列會傳送至 `dotnet complete` 命令，並由您的殼層處理結果。 您可以直接傳送某些內容至 `dotnet complete` 命令來測試結果，而不啟用 tab 鍵自動完成。 例如：

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

如果該命令無法運作，請確定已安裝 .NET Core 2.0 SDK 或更新版本。 如果已安裝，但該命令仍無法運作，請確定 `dotnet` 命令會解析為 .NET Core 2.0 SDK 版和更新版本。 使用 `dotnet --version` 命令來查看目前路徑將解析為哪個 `dotnet` 版本。 如需詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md)。

### <a name="examples"></a>範例

以下是 tab 鍵自動完成所提供的一些範例：

輸入                                | 變成                                                                     | 因為
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` 依字母順序是第一個子命令。
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Tab 鍵自動完成會比對子字串，且依字母順序首先會出現 `--help`。
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | 再按一次 tab 鍵會顯示下一個建議。      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | 結果會依字母順序傳回。
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Tab 鍵自動完成會感知專案檔。

## <a name="powershell"></a>PowerShell

若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **PowerShell**，請建立設定檔或編輯儲存在變數 `$PROFILE` 中的設定檔。 如需詳細資訊，請參閱[如何建立設定檔](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile)和[設定檔與執行原則](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy)。 

將下列程式碼新增至您的設定檔：

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>Bash

若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **bash** 殼層，請將下列程式碼新增至您的 `.bashrc` 檔案：

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}")"

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>Zsh

若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **zsh** 殼層，請將下列程式碼新增至您的 `.zshrc` 檔案：

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
