---
title: 啟用 TAB 鍵自動完成
description: 本文描述如何為適用於 PowerShell、Bash 和 zsh 的 .NET Core CLI 啟用 tab 鍵自動完成。
author: adegeo
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 491e1ca34c20c3994a571fc2deff7392c6bdb3f2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324388"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a>如何為 .NET Core CLI 啟用 TAB 鍵自動完成

**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

本文描述如何為 PowerShell、Bash 和 zsh 等三種殼層設定 tab 鍵自動完成。 如需其他 shell，請參閱其檔，以瞭解如何設定 tab 鍵自動完成。

設定完成後，您可以 `dotnet` 在 shell 中輸入命令，然後按下 tab 鍵，來觸發 .NET Core CLI 的 tab 鍵自動完成。 目前的命令列會傳送至 `dotnet complete` 命令，並由您的殼層處理結果。 您可以直接傳送某些內容至 `dotnet complete` 命令來測試結果，而不啟用 tab 鍵自動完成。 例如：

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

若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **PowerShell**，請建立設定檔或編輯儲存在變數 `$PROFILE` 中的設定檔。 如需詳細資訊，請參閱[如何建立設定檔](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile)和[設定檔與執行原則](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)。

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
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>zsh

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
