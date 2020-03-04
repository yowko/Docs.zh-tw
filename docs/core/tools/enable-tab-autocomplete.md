---
title: 啟用 TAB 鍵自動完成
description: 本文描述如何為適用於 PowerShell、Bash 和 zsh 的 .NET Core CLI 啟用 tab 鍵自動完成。
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 31328be14811760bc8d7fb527e0d55abfe6b1493
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156747"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a><span data-ttu-id="fe13b-103">如何為 .NET Core CLI 啟用 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="fe13b-103">How to enable TAB completion for the .NET Core CLI</span></span>

<span data-ttu-id="fe13b-104">**本文適用于：** ✔️ .net CORE 2.1 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="fe13b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="fe13b-105">本文描述如何為 PowerShell、Bash 和 zsh 等三種殼層設定 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="fe13b-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="fe13b-106">如需其他 shell，請參閱其檔，以瞭解如何設定 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="fe13b-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="fe13b-107">設定完成後，您可以在 shell 中輸入 `dotnet` 命令，然後按下 TAB 鍵，來觸發 .NET Core CLI 的 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="fe13b-107">Once set up, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="fe13b-108">目前的命令列會傳送至 `dotnet complete` 命令，並由您的殼層處理結果。</span><span class="sxs-lookup"><span data-stu-id="fe13b-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="fe13b-109">您可以直接傳送某些內容至 `dotnet complete` 命令來測試結果，而不啟用 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="fe13b-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="fe13b-110">例如：</span><span class="sxs-lookup"><span data-stu-id="fe13b-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="fe13b-111">如果該命令無法運作，請確定已安裝 .NET Core 2.0 SDK 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="fe13b-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="fe13b-112">如果已安裝，但該命令仍無法運作，請確定 `dotnet` 命令會解析為 .NET Core 2.0 SDK 版和更新版本。</span><span class="sxs-lookup"><span data-stu-id="fe13b-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="fe13b-113">使用 `dotnet --version` 命令來查看目前路徑將解析為哪個 `dotnet` 版本。</span><span class="sxs-lookup"><span data-stu-id="fe13b-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="fe13b-114">如需詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md)。</span><span class="sxs-lookup"><span data-stu-id="fe13b-114">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="fe13b-115">範例</span><span class="sxs-lookup"><span data-stu-id="fe13b-115">Examples</span></span>

<span data-ttu-id="fe13b-116">以下是 tab 鍵自動完成所提供的一些範例：</span><span class="sxs-lookup"><span data-stu-id="fe13b-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="fe13b-117">輸入</span><span class="sxs-lookup"><span data-stu-id="fe13b-117">Input</span></span>                                | <span data-ttu-id="fe13b-118">變成</span><span class="sxs-lookup"><span data-stu-id="fe13b-118">becomes</span></span>                                                                     | <span data-ttu-id="fe13b-119">因為</span><span class="sxs-lookup"><span data-stu-id="fe13b-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="fe13b-120">`add` 依字母順序是第一個子命令。</span><span class="sxs-lookup"><span data-stu-id="fe13b-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="fe13b-121">Tab 鍵自動完成會比對子字串，且依字母順序首先會出現 `--help`。</span><span class="sxs-lookup"><span data-stu-id="fe13b-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="fe13b-122">再按一次 tab 鍵會顯示下一個建議。</span><span class="sxs-lookup"><span data-stu-id="fe13b-122">Pressing tab a second time brings up the next suggestion.</span></span>
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="fe13b-123">結果會依字母順序傳回。</span><span class="sxs-lookup"><span data-stu-id="fe13b-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="fe13b-124">Tab 鍵自動完成會感知專案檔。</span><span class="sxs-lookup"><span data-stu-id="fe13b-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="fe13b-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe13b-125">PowerShell</span></span>

<span data-ttu-id="fe13b-126">若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **PowerShell**，請建立設定檔或編輯儲存在變數 `$PROFILE` 中的設定檔。</span><span class="sxs-lookup"><span data-stu-id="fe13b-126">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="fe13b-127">如需詳細資訊，請參閱[如何建立設定檔](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile)和[設定檔與執行原則](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)。</span><span class="sxs-lookup"><span data-stu-id="fe13b-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span>

<span data-ttu-id="fe13b-128">將下列程式碼新增至您的設定檔：</span><span class="sxs-lookup"><span data-stu-id="fe13b-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="fe13b-129">Bash</span><span class="sxs-lookup"><span data-stu-id="fe13b-129">bash</span></span>

<span data-ttu-id="fe13b-130">若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **bash** 殼層，請將下列程式碼新增至您的 `.bashrc` 檔案：</span><span class="sxs-lookup"><span data-stu-id="fe13b-130">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="fe13b-131">zsh</span><span class="sxs-lookup"><span data-stu-id="fe13b-131">zsh</span></span>

<span data-ttu-id="fe13b-132">若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **zsh** 殼層，請將下列程式碼新增至您的 `.zshrc` 檔案：</span><span class="sxs-lookup"><span data-stu-id="fe13b-132">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
