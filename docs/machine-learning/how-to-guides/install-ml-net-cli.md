---
title: 如何安裝 ML.NET 命令列介面 (CLI) 工具
description: 瞭解如何安裝、升級、降級和卸載ML.NET命令列介面 （CLI） 工具。
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848635"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="f558a-103">如何安裝 ML.NET 命令列介面 (CLI) 工具</span><span class="sxs-lookup"><span data-stu-id="f558a-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="f558a-104">瞭解如何在 Windows、Mac 或 Linux 上安裝ML.NET CLI（命令列介面）。</span><span class="sxs-lookup"><span data-stu-id="f558a-104">Learn how to install the ML.NET CLI (command-line interface) on Windows, Mac, or Linux.</span></span>

<span data-ttu-id="f558a-105">ML.NET CLI 使用自動機器學習 （AutoML） 和培訓資料集生成高品質ML.NET模型和原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="f558a-105">The ML.NET CLI generates good quality ML.NET models and source code using automated machine learning (AutoML) and a training dataset.</span></span>

> [!NOTE]
> <span data-ttu-id="f558a-106">本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="f558a-106">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="f558a-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="f558a-107">Pre-requisites</span></span>

- [<span data-ttu-id="f558a-108">.NET Core 2.2 SDK</span><span class="sxs-lookup"><span data-stu-id="f558a-108">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="f558a-109">(選擇性) [Visual Studio 2017 或 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="f558a-109">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="f558a-110">您可以通過按`F5`鍵或使用`dotnet run`（.NET 核心 CLI）使用 Visual Studio 運行生成的 C# 代碼專案。</span><span class="sxs-lookup"><span data-stu-id="f558a-110">You can run the generated C# code projects with Visual Studio by pressing the `F5` key or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="f558a-111">注意：如果在安裝[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)後，`dotnet tool`該命令不起作用，請從 Windows 登出並重新登錄。</span><span class="sxs-lookup"><span data-stu-id="f558a-111">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="f558a-112">安裝</span><span class="sxs-lookup"><span data-stu-id="f558a-112">Install</span></span>

<span data-ttu-id="f558a-113">ML.NET CLI 的安裝就像任何其他 dotnet 通用工具。</span><span class="sxs-lookup"><span data-stu-id="f558a-113">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="f558a-114">您會使用 `dotnet tool install` .NET Core CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="f558a-114">You use the `dotnet tool install` .NET Core CLI command.</span></span>

<span data-ttu-id="f558a-115">下列範例示範如何在 NuGet 摘要位置中安裝 ML.NET CLI：</span><span class="sxs-lookup"><span data-stu-id="f558a-115">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="f558a-116">如果無法安裝此工具 (亦即如果它無法自預設的 NuGet 摘要取得)，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f558a-116">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="f558a-117">請確認正在檢查您所預期的摘要。</span><span class="sxs-lookup"><span data-stu-id="f558a-117">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="f558a-118">如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：</span><span class="sxs-lookup"><span data-stu-id="f558a-118">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="f558a-119">您可以鍵入下列命令確認安裝是否成功：</span><span class="sxs-lookup"><span data-stu-id="f558a-119">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="f558a-120">您應該會看到 mlnet 工具可用命令的說明，例如 'auto-train' 命令。</span><span class="sxs-lookup"><span data-stu-id="f558a-120">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="f558a-121">安裝特定的發行版本</span><span class="sxs-lookup"><span data-stu-id="f558a-121">Install a specific release version</span></span>

<span data-ttu-id="f558a-122">如果您要嘗試安裝發行前版本或特定版本的工具，可以使用下列格式指定[架構](../../standard/frameworks.md)：</span><span class="sxs-lookup"><span data-stu-id="f558a-122">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="f558a-123">您也可以鍵入下列命令，檢查套件是否正確安裝：</span><span class="sxs-lookup"><span data-stu-id="f558a-123">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="f558a-124">解除安裝 CLI 套件</span><span class="sxs-lookup"><span data-stu-id="f558a-124">Uninstall the CLI package</span></span>

<span data-ttu-id="f558a-125">鍵入下列命令，從本機電腦解除安裝套件：</span><span class="sxs-lookup"><span data-stu-id="f558a-125">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="f558a-126">更新 CLI 套件</span><span class="sxs-lookup"><span data-stu-id="f558a-126">Update the CLI package</span></span>

<span data-ttu-id="f558a-127">鍵入下列命令，從本機電腦更新套件：</span><span class="sxs-lookup"><span data-stu-id="f558a-127">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="f558a-128">設定 CLI 建議 (tab 鍵自動完成)</span><span class="sxs-lookup"><span data-stu-id="f558a-128">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="f558a-129">因為 ML.NET CLI 是以 `System.CommandLine` 為基礎，所以它有內建的 tab 鍵自動完成支援。</span><span class="sxs-lookup"><span data-stu-id="f558a-129">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="f558a-130">下列動畫展示 tab 鍵自動完成運作範例：</span><span class="sxs-lookup"><span data-stu-id="f558a-130">An example of how tab auto completion works is shown in the following animation:</span></span>

![image](./media/cli-tab-completion.gif)

<span data-ttu-id="f558a-132">「tab 鍵自動完成」(參數建議) 適用於 *Windows PowerShell* 和 *macOS/Linux bash*，但不適用於 *Windows CMD*。</span><span class="sxs-lookup"><span data-stu-id="f558a-132">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="f558a-133">若要啟用它，在目前的預覽版本中，終端使用者必須針對每個 shell 各採取一些步驟，如下所述。</span><span class="sxs-lookup"><span data-stu-id="f558a-133">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="f558a-134">完成此作業後，使用 `System.CommandLine` 撰寫的所有應用程式，例如 ML.NET CLI，都會執行完成。</span><span class="sxs-lookup"><span data-stu-id="f558a-134">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="f558a-135">在您想要啟用完成的電腦上，您需要做兩件事。</span><span class="sxs-lookup"><span data-stu-id="f558a-135">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="f558a-136">執行下列命令以安裝 `dotnet-suggest` 通用工具：</span><span class="sxs-lookup"><span data-stu-id="f558a-136">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="f558a-137">將適當的填充碼指令碼新增至 shell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="f558a-137">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="f558a-138">您可能必須建立 shell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="f558a-138">You may have to create a shell profile file.</span></span> <span data-ttu-id="f558a-139">填充碼指令碼會將完成要求，從您的 shell 轉送至 `dotnet-suggest`工具，委派給 `System.CommandLine` 型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f558a-139">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="f558a-140">若是 Bash，請將 [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) 的內容新增至 `~/.bash_profile`。</span><span class="sxs-lookup"><span data-stu-id="f558a-140">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="f558a-141">若為 PowerShell，請將 [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) 的內容新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="f558a-141">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="f558a-142">您可在主控台中執行下列命令，找到 PowerShell 設定檔的預期路徑：</span><span class="sxs-lookup"><span data-stu-id="f558a-142">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ```

<span data-ttu-id="f558a-143">(若為其他 shell，請[尋求](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22)或提出[問題](https://github.com/dotnet/System.CommandLine/issues)。)</span><span class="sxs-lookup"><span data-stu-id="f558a-143">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="f558a-144">安裝目錄</span><span class="sxs-lookup"><span data-stu-id="f558a-144">Installation directory</span></span>

<span data-ttu-id="f558a-145">ML.NET CLI 可以安裝在預設目錄或特定位置。</span><span class="sxs-lookup"><span data-stu-id="f558a-145">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="f558a-146">預設目錄如下：</span><span class="sxs-lookup"><span data-stu-id="f558a-146">The default directories are:</span></span>

| <span data-ttu-id="f558a-147">OS</span><span class="sxs-lookup"><span data-stu-id="f558a-147">OS</span></span>          | <span data-ttu-id="f558a-148">Path</span><span class="sxs-lookup"><span data-stu-id="f558a-148">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="f558a-149">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="f558a-149">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="f558a-150">Windows</span><span class="sxs-lookup"><span data-stu-id="f558a-150">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="f558a-151">第一次執行 SDK　時，這些位置會新增至使用者的路徑，因此可以直接呼叫安裝在該處的通用工具。</span><span class="sxs-lookup"><span data-stu-id="f558a-151">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="f558a-152">請注意，通用工具是使用者特定工具，而不是電腦全域工具。</span><span class="sxs-lookup"><span data-stu-id="f558a-152">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="f558a-153">使用者特定表示您無法安裝可供電腦上所有使用者使用的通用工具。</span><span class="sxs-lookup"><span data-stu-id="f558a-153">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="f558a-154">此工具只適用於已安裝工具的每個使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="f558a-154">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="f558a-155">通用工具也可以安裝在特定目錄中。</span><span class="sxs-lookup"><span data-stu-id="f558a-155">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="f558a-156">安裝在特定目錄時，使用者必須確保命令可用，方法是在路徑中包含該目錄、使用指定的目錄呼叫命令，或從指定的目錄中呼叫工具。</span><span class="sxs-lookup"><span data-stu-id="f558a-156">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="f558a-157">在此情況下，.NET Core CLI 不會將這個位置自動新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="f558a-157">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="f558a-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f558a-158">See also</span></span>

- [<span data-ttu-id="f558a-159">ML.NET CLI 概述</span><span class="sxs-lookup"><span data-stu-id="f558a-159">ML.NET CLI overview</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="f558a-160">教程：使用 cLI ML.NET 分析情緒</span><span class="sxs-lookup"><span data-stu-id="f558a-160">Tutorial: Analyze sentiment with the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="f558a-161">ML.NET CLI auto-train 命令參考指南</span><span class="sxs-lookup"><span data-stu-id="f558a-161">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="f558a-162">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="f558a-162">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
