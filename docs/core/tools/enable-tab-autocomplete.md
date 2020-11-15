---
title: 啟用 TAB 鍵自動完成
description: 本文會教您如何針對 PowerShell、Bash 和 zsh 啟用適用于 .NET CLI 的 tab 鍵自動完成。
author: adegeo
ms.author: adegeo
ms.topic: how-to
ms.date: 11/03/2019
ms.openlocfilehash: 31bf5e74644680fc30ca5b79972fbed6367363e1
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634008"
---
# <a name="how-to-enable-tab-completion-for-the-net-cli"></a>如何啟用 .NET CLI 的 TAB 鍵自動完成

本文 **適用于：** ✔️ .net CORE 2.1 SDK 和更新版本

本文描述如何為 PowerShell、Bash 和 zsh 等三種殼層設定 tab 鍵自動完成。 針對其他 shell，請參閱其檔，以瞭解如何設定 tab 鍵自動完成。

設定完成之後，在 shell 中輸入 `dotnet` 命令，然後按下 tab 鍵，就會觸發 .NET CLI 的 tab 鍵自動完成。 目前的命令列會傳送至 `dotnet complete` 命令，並由您的殼層處理結果。 您可以直接傳送某些內容至 `dotnet complete` 命令來測試結果，而不啟用 tab 鍵自動完成。 例如：

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

如果該命令無法運作，請確定已安裝 .NET Core 2.0 SDK 或更新版本。 如果已安裝，但該命令仍無法運作，請確定 `dotnet` 命令會解析為 .NET Core 2.0 SDK 版和更新版本。 使用 `dotnet --version` 命令來查看目前路徑將解析為哪個 `dotnet` 版本。 如需詳細資訊，請參閱 [選取要使用的 .net 版本](../versions/selection.md)。

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

若要將 tab 鍵自動完成新增至 .NET CLI 的 **PowerShell** ，請建立或編輯儲存在變數中的設定檔 `$PROFILE` 。 如需詳細資訊，請參閱[如何建立設定檔](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile)和[設定檔與執行原則](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)。

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

若要將 tab 鍵自動完成新增至 .NET CLI 的 **bash** shell，請將下列程式碼新增至您的檔案 `.bashrc` ：

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

若要將 tab 鍵自動完成新增至 .NET CLI 的 **zsh** shell，請將下列程式碼新增至您的檔案 `.zshrc` ：

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
