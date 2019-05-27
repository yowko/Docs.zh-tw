---
title: 如何安裝 ML.NET 命令列介面 (CLI) 工具
description: ML.NET 命令列介面 (CLI) 工具的概觀與安裝。
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 9560aa846a1aefabadbd7d4faf8bd306ba72e0de
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557864"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="24e34-103">如何安裝 ML.NET 命令列介面 (CLI) 工具</span><span class="sxs-lookup"><span data-stu-id="24e34-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="24e34-104">ML.NET CLI (命令列介面) 是您可以在任何命令提示字元 (Windows、Mac 或 Linux) 中執行的工具，根據您提供的定型資料集產生高品質 ML.NET 模型和原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="24e34-104">The ML.NET CLI (command-line interface) is a tool you can run on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on training datasets you provide.</span></span>

> [!NOTE]
> <span data-ttu-id="24e34-105">本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="24e34-105">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="24e34-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="24e34-106">Pre-requisites</span></span>

- [<span data-ttu-id="24e34-107">.NET Core 2.2 SDK</span><span class="sxs-lookup"><span data-stu-id="24e34-107">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="24e34-108">(選擇性) [Visual Studio 2017 或 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="24e34-108">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="24e34-109">您可以使用 Visual Studio F5 或 `dotnet run` (.NET Core CLI) 執行已產生的 C# 程式碼專案。</span><span class="sxs-lookup"><span data-stu-id="24e34-109">You can either run the generated C# code projects with Visual Studio F5 or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="24e34-110">注意:如果在安裝 [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) 後，`dotnet tool` 命令無法運作，請登出 Windows，並再次登入。</span><span class="sxs-lookup"><span data-stu-id="24e34-110">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="24e34-111">安裝</span><span class="sxs-lookup"><span data-stu-id="24e34-111">Install</span></span>

<span data-ttu-id="24e34-112">ML.NET CLI 的安裝就像任何其他 dotnet 通用工具。</span><span class="sxs-lookup"><span data-stu-id="24e34-112">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="24e34-113">您會使用 `dotnet tool install` .NET Core CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="24e34-113">You use the `dotnet tool install` .NET Core CLI command.</span></span> 

<span data-ttu-id="24e34-114">下列範例示範如何在 NuGet 摘要位置中安裝 ML.NET CLI：</span><span class="sxs-lookup"><span data-stu-id="24e34-114">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```console
> dotnet tool install -g mlnet
```

<span data-ttu-id="24e34-115">如果無法安裝此工具 (亦即如果它無法自預設的 NuGet 摘要取得)，則會顯示錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="24e34-115">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="24e34-116">請確認正在檢查您所預期的摘要。</span><span class="sxs-lookup"><span data-stu-id="24e34-116">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="24e34-117">如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：</span><span class="sxs-lookup"><span data-stu-id="24e34-117">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="24e34-118">您可以鍵入下列命令確認安裝是否成功：</span><span class="sxs-lookup"><span data-stu-id="24e34-118">You can confirm the installation was successful by typing the following command:</span></span>

```console
> mlnet
```

<span data-ttu-id="24e34-119">您應該會看到 mlnet 工具可用命令的說明，例如 'auto-train' 命令。</span><span class="sxs-lookup"><span data-stu-id="24e34-119">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="24e34-120">安裝特定的發行版本</span><span class="sxs-lookup"><span data-stu-id="24e34-120">Install a specific release version</span></span>

<span data-ttu-id="24e34-121">如果您要嘗試安裝發行前版本或特定版本的工具，可以使用下列格式指定[架構](../../standard/frameworks.md)：</span><span class="sxs-lookup"><span data-stu-id="24e34-121">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```console
> dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="24e34-122">您也可以鍵入下列命令，檢查套件是否正確安裝：</span><span class="sxs-lookup"><span data-stu-id="24e34-122">You can also check if the package is properly installed by typing the following command:</span></span>

```console
> dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="24e34-123">解除安裝 CLI 套件</span><span class="sxs-lookup"><span data-stu-id="24e34-123">Uninstall the CLI package</span></span>

<span data-ttu-id="24e34-124">鍵入下列命令，從本機電腦解除安裝套件：</span><span class="sxs-lookup"><span data-stu-id="24e34-124">Type the following command to uninstall the package from your local machine:</span></span>

```console
> dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="24e34-125">更新 CLI 套件</span><span class="sxs-lookup"><span data-stu-id="24e34-125">Update the CLI package</span></span>

<span data-ttu-id="24e34-126">鍵入下列命令，從本機電腦更新套件：</span><span class="sxs-lookup"><span data-stu-id="24e34-126">Type the following command to update the package from your local machine:</span></span>

```console
> dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="24e34-127">設定 CLI 建議 (tab 鍵自動完成)</span><span class="sxs-lookup"><span data-stu-id="24e34-127">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="24e34-128">因為 ML.NET CLI 是以 `System.CommandLine` 為基礎，所以它有內建的 tab 鍵自動完成支援。</span><span class="sxs-lookup"><span data-stu-id="24e34-128">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="24e34-129">下列動畫展示 tab 鍵自動完成運作範例：</span><span class="sxs-lookup"><span data-stu-id="24e34-129">An example of how tab auto completion works is shown in the following animation:</span></span>

![影像](./media/cli-tab-completion.gif)

<span data-ttu-id="24e34-131">「tab 鍵自動完成」(參數建議) 適用於 *Windows PowerShell* 和 *macOS/Linux bash*，但不適用於 *Windows CMD*。</span><span class="sxs-lookup"><span data-stu-id="24e34-131">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="24e34-132">若要啟用它，在目前的預覽版本中，終端使用者必須針對每個 shell 各採取一些步驟，如下所述。</span><span class="sxs-lookup"><span data-stu-id="24e34-132">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="24e34-133">完成此作業後，使用 `System.CommandLine` 撰寫的所有應用程式，例如 ML.NET CLI，都會執行完成。</span><span class="sxs-lookup"><span data-stu-id="24e34-133">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="24e34-134">在您想要啟用完成的電腦上，您需要做兩件事。</span><span class="sxs-lookup"><span data-stu-id="24e34-134">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="24e34-135">執行下列命令以安裝 `dotnet-suggest` 通用工具：</span><span class="sxs-lookup"><span data-stu-id="24e34-135">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```console
    > dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="24e34-136">將適當的填充碼指令碼新增至 shell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="24e34-136">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="24e34-137">您可能必須建立 shell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="24e34-137">You may have to create a shell profile file.</span></span> <span data-ttu-id="24e34-138">填充碼指令碼會將完成要求，從您的 shell 轉送至 `dotnet-suggest`工具，委派給 `System.CommandLine` 型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="24e34-138">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    * <span data-ttu-id="24e34-139">若是 Bash，請將 [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) 的內容新增至 `~/.bash_profile`。</span><span class="sxs-lookup"><span data-stu-id="24e34-139">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    * <span data-ttu-id="24e34-140">若為 PowerShell，請將 [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) 的內容新增至您的 PowerShell 設定檔。</span><span class="sxs-lookup"><span data-stu-id="24e34-140">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="24e34-141">您可在主控台中執行下列命令，找到 PowerShell 設定檔的預期路徑：</span><span class="sxs-lookup"><span data-stu-id="24e34-141">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    > echo $profile
    ``` 

<span data-ttu-id="24e34-142">(若為其他 shell，請[尋求](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22)或提出[問題](https://github.com/dotnet/System.CommandLine/issues)。)</span><span class="sxs-lookup"><span data-stu-id="24e34-142">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="24e34-143">安裝目錄</span><span class="sxs-lookup"><span data-stu-id="24e34-143">Installation directory</span></span>

<span data-ttu-id="24e34-144">ML.NET CLI 可以安裝在預設目錄或特定位置。</span><span class="sxs-lookup"><span data-stu-id="24e34-144">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="24e34-145">預設目錄如下：</span><span class="sxs-lookup"><span data-stu-id="24e34-145">The default directories are:</span></span>

| <span data-ttu-id="24e34-146">作業系統</span><span class="sxs-lookup"><span data-stu-id="24e34-146">OS</span></span>          | <span data-ttu-id="24e34-147">路徑</span><span class="sxs-lookup"><span data-stu-id="24e34-147">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="24e34-148">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="24e34-148">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="24e34-149">Windows</span><span class="sxs-lookup"><span data-stu-id="24e34-149">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="24e34-150">第一次執行 SDK　時，這些位置會新增至使用者的路徑，因此可以直接呼叫安裝在該處的通用工具。</span><span class="sxs-lookup"><span data-stu-id="24e34-150">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="24e34-151">請注意，通用工具是使用者特定工具，而不是電腦全域工具。</span><span class="sxs-lookup"><span data-stu-id="24e34-151">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="24e34-152">使用者特定表示您無法安裝可供電腦上所有使用者使用的通用工具。</span><span class="sxs-lookup"><span data-stu-id="24e34-152">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="24e34-153">此工具只適用於已安裝工具的每個使用者設定檔。</span><span class="sxs-lookup"><span data-stu-id="24e34-153">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="24e34-154">通用工具也可以安裝在特定目錄中。</span><span class="sxs-lookup"><span data-stu-id="24e34-154">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="24e34-155">安裝在特定目錄時，使用者必須確保命令可用，方法是在路徑中包含該目錄、使用指定的目錄呼叫命令，或從指定的目錄中呼叫工具。</span><span class="sxs-lookup"><span data-stu-id="24e34-155">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="24e34-156">在此情況下，.NET Core CLI 不會將這個位置自動新增至 PATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="24e34-156">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="24e34-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24e34-157">See also</span></span>

- [<span data-ttu-id="24e34-158">＜ML.NET CLI 工具使用者入門＞的教學課程</span><span class="sxs-lookup"><span data-stu-id="24e34-158">Tutorial on 'Getting Started with ML.NET CLI tool'</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="24e34-159">如何使用 ML.NET CLI 工具自動定型模型</span><span class="sxs-lookup"><span data-stu-id="24e34-159">How to automatically train models with the ML.NET CLI tool</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="24e34-160">ML.NET CLI 自動定型命令參考指南</span><span class="sxs-lookup"><span data-stu-id="24e34-160">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="24e34-161">ML.NET CLI 中的遙測</span><span class="sxs-lookup"><span data-stu-id="24e34-161">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
