---
title: 啟用 tab 鍵自動完成
description: 本文描述如何為適用於 PowerShell、Bash 和 zsh 的 .NET Core CLI 啟用 tab 鍵自動完成。
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 0f29ba2ef1d419339a0e2dc44f67c93b326eb40d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182465"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="3fce1-103">如何為 .NET Core CLI 啟用 TAB 鍵自動完成</span><span class="sxs-lookup"><span data-stu-id="3fce1-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="3fce1-104">從 .NET Core 2.0 SDK 開始，.NET Core CLI 支援 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="3fce1-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="3fce1-105">本文描述如何為 PowerShell、Bash 和 zsh 等三種殼層設定 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="3fce1-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="3fce1-106">其他殼層可能支援自動完成。</span><span class="sxs-lookup"><span data-stu-id="3fce1-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="3fce1-107">請參閱其文件以了解如何設定自動完成，其中的步驟應該會類似於本文中所述的步驟。</span><span class="sxs-lookup"><span data-stu-id="3fce1-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="3fce1-108">設定後，只要在殼層中輸入 `dotnet` 命令，然後按 TAB 鍵，即會觸發 .NET Core CLI 的 Tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="3fce1-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="3fce1-109">目前的命令列會傳送至 `dotnet complete` 命令，並由您的殼層處理結果。</span><span class="sxs-lookup"><span data-stu-id="3fce1-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="3fce1-110">您可以直接傳送某些內容至 `dotnet complete` 命令來測試結果，而不啟用 tab 鍵自動完成。</span><span class="sxs-lookup"><span data-stu-id="3fce1-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="3fce1-111">例如：</span><span class="sxs-lookup"><span data-stu-id="3fce1-111">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="3fce1-112">如果該命令無法運作，請確定已安裝 .NET Core 2.0 SDK 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="3fce1-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="3fce1-113">如果已安裝，但該命令仍無法運作，請確定 `dotnet` 命令會解析為 .NET Core 2.0 SDK 版和更新版本。</span><span class="sxs-lookup"><span data-stu-id="3fce1-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="3fce1-114">使用 `dotnet --version` 命令來查看目前路徑將解析為哪個 `dotnet` 版本。</span><span class="sxs-lookup"><span data-stu-id="3fce1-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="3fce1-115">如需詳細資訊，請參閱[選取要使用的 .NET Core 版本](../versions/selection.md)。</span><span class="sxs-lookup"><span data-stu-id="3fce1-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="3fce1-116">範例</span><span class="sxs-lookup"><span data-stu-id="3fce1-116">Examples</span></span>

<span data-ttu-id="3fce1-117">以下是 tab 鍵自動完成所提供的一些範例：</span><span class="sxs-lookup"><span data-stu-id="3fce1-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="3fce1-118">輸入</span><span class="sxs-lookup"><span data-stu-id="3fce1-118">Input</span></span>                                | <span data-ttu-id="3fce1-119">變成</span><span class="sxs-lookup"><span data-stu-id="3fce1-119">becomes</span></span>                                                                     | <span data-ttu-id="3fce1-120">因為</span><span class="sxs-lookup"><span data-stu-id="3fce1-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="3fce1-121">`add` 依字母順序是第一個子命令。</span><span class="sxs-lookup"><span data-stu-id="3fce1-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="3fce1-122">Tab 鍵自動完成會比對子字串，且依字母順序首先會出現 `--help`。</span><span class="sxs-lookup"><span data-stu-id="3fce1-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="3fce1-123">再按一次 tab 鍵會顯示下一個建議。</span><span class="sxs-lookup"><span data-stu-id="3fce1-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="3fce1-124">結果會依字母順序傳回。</span><span class="sxs-lookup"><span data-stu-id="3fce1-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="3fce1-125">Tab 鍵自動完成會感知專案檔。</span><span class="sxs-lookup"><span data-stu-id="3fce1-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="3fce1-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3fce1-126">PowerShell</span></span>

<span data-ttu-id="3fce1-127">若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **PowerShell**，請建立設定檔或編輯儲存在變數 `$PROFILE` 中的設定檔。</span><span class="sxs-lookup"><span data-stu-id="3fce1-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="3fce1-128">如需詳細資訊，請參閱[如何建立設定檔](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile)和[設定檔與執行原則](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)。</span><span class="sxs-lookup"><span data-stu-id="3fce1-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="3fce1-129">將下列程式碼新增至您的設定檔：</span><span class="sxs-lookup"><span data-stu-id="3fce1-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="3fce1-130">Bash</span><span class="sxs-lookup"><span data-stu-id="3fce1-130">Bash</span></span>

<span data-ttu-id="3fce1-131">若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **bash** 殼層，請將下列程式碼新增至您的 `.bashrc` 檔案：</span><span class="sxs-lookup"><span data-stu-id="3fce1-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="3fce1-132">Zsh</span><span class="sxs-lookup"><span data-stu-id="3fce1-132">Zsh</span></span>

<span data-ttu-id="3fce1-133">若要將 tab 鍵自動完成新增至 .NET Core CLI 的 **zsh** 殼層，請將下列程式碼新增至您的 `.zshrc` 檔案：</span><span class="sxs-lookup"><span data-stu-id="3fce1-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
