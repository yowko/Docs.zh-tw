---
title: global.json 概觀
description: 了解如何使用 global.json 檔案來設定執行.NET Core CLI 命令時的 NET Core SDK 版本。
ms.date: 12/03/2018
ms.custom: updateeachrelease, seodec18
ms.openlocfilehash: e0f929a049812cac6f62e5218629c9b0add83de8
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170765"
---
# <a name="globaljson-overview"></a><span data-ttu-id="a9def-103">global.json 概觀</span><span class="sxs-lookup"><span data-stu-id="a9def-103">global.json overview</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

<span data-ttu-id="a9def-104">*global.json* 檔案可讓您定義執行.NET Core CLI 命令時所使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-104">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="a9def-105">選取 .NET Core SDK 與指定專案所針對的執行階段沒有關係。</span><span class="sxs-lookup"><span data-stu-id="a9def-105">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="a9def-106">.NET Core SDK 版本會指出使用哪個版本的.NET Core CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="a9def-106">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span> <span data-ttu-id="a9def-107">一般情況下，您要使用最新版本的工具，所以不需要 *global.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="a9def-107">In general, you want to use the latest version of the tools, so no *global.json* file is needed.</span></span>

<span data-ttu-id="a9def-108">如需改為指定執行階段的詳細資訊，請參閱[目標架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="a9def-108">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="a9def-109">.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找 *global.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="a9def-109">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="a9def-110">global.json 結構描述</span><span class="sxs-lookup"><span data-stu-id="a9def-110">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="a9def-111">SDK</span><span class="sxs-lookup"><span data-stu-id="a9def-111">sdk</span></span>

<span data-ttu-id="a9def-112">類型：Object</span><span class="sxs-lookup"><span data-stu-id="a9def-112">Type: Object</span></span>

<span data-ttu-id="a9def-113">指定要選取 .NET Core SDK 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a9def-113">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="a9def-114">版本</span><span class="sxs-lookup"><span data-stu-id="a9def-114">version</span></span>

<span data-ttu-id="a9def-115">類型：String</span><span class="sxs-lookup"><span data-stu-id="a9def-115">Type: String</span></span>

<span data-ttu-id="a9def-116">要使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-116">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="a9def-117">請注意，此欄位：</span><span class="sxs-lookup"><span data-stu-id="a9def-117">Note that this field:</span></span>

- <span data-ttu-id="a9def-118">不支援萬用字元，亦即，必須指定完整的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a9def-118">Doesn't have globbing support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="a9def-119">不支援版本範圍。</span><span class="sxs-lookup"><span data-stu-id="a9def-119">Doesn't support version ranges.</span></span>

<span data-ttu-id="a9def-120">下列範例顯示 *global.json* 檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="a9def-120">The following example shows the contents of a *global.json* file:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="a9def-121">global.json 和.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a9def-121">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="a9def-122">最好知道哪一個版本可供使用，以便在 *global.json* 檔案中設定一個。</span><span class="sxs-lookup"><span data-stu-id="a9def-122">It's helpful to know which versions are available in order to set one in the *global.json* file.</span></span> <span data-ttu-id="a9def-123">您可以在 [.NET 下載](https://www.microsoft.com/net/download/all)網站找到 SDK 支援版本的完整清單。</span><span class="sxs-lookup"><span data-stu-id="a9def-123">You can find the full list of supported available SDKs at the [.NET Downloads](https://www.microsoft.com/net/download/all) site.</span></span> <span data-ttu-id="a9def-124">從 .NET Core 2.1 SDK 開始，您可以執行下列命令來確認電腦上已經安裝的 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="a9def-124">Starting with .NET Core 2.1 SDK, you can run the following command to verify which SDK versions are already installed on your machine:</span></span>

```console
dotnet --list-sdks
```

<span data-ttu-id="a9def-125">若要在電腦上安裝其他 .NET Core SDK 版本，請造訪 [.NET 下載](https://www.microsoft.com/net/download/all)網站。</span><span class="sxs-lookup"><span data-stu-id="a9def-125">To install additional .NET Core SDK versions on your machine, visit the [.NET Downloads](https://www.microsoft.com/net/download/all) site.</span></span>

<span data-ttu-id="a9def-126">執行 [dotnet new](dotnet-new.md) 命令，可在目前的目錄中建立新的 *global.json* 檔案，與下面的範例類似：</span><span class="sxs-lookup"><span data-stu-id="a9def-126">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```console
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a><span data-ttu-id="a9def-127">比對規則</span><span class="sxs-lookup"><span data-stu-id="a9def-127">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="a9def-128">比對規則由 apphost 規範，這是.NET Core 執行階段的一部分。</span><span class="sxs-lookup"><span data-stu-id="a9def-128">The matching rules are governed by the apphost, which is part of the .NET Core runtime.</span></span>
> <span data-ttu-id="a9def-129">您有多個執行階段並列安裝時，會使用最新版本的主機。</span><span class="sxs-lookup"><span data-stu-id="a9def-129">The latest version of the host is used when you have multiple runtimes installed side-by-side.</span></span>

<span data-ttu-id="a9def-130">從 .NET Core 2.0 開始，決定要使用哪個 SDK 版本時會使用下列規則：</span><span class="sxs-lookup"><span data-stu-id="a9def-130">Starting with .NET Core 2.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="a9def-131">如果找不到 *global.json* 檔案或 *global.json* 沒有指定 SDK 版本，則會使用最新安裝的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-131">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="a9def-132">最新的 SDK 版本可以是發行版本或發行前版本，而最高版本號碼優先採用。</span><span class="sxs-lookup"><span data-stu-id="a9def-132">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>
- <span data-ttu-id="a9def-133">如果 *global.json* 未指定 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="a9def-133">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="a9def-134">如果在電腦上找到了指定的 SDK 版本，則會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-134">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="a9def-135">如果在電腦上找不到指定的 SDK 版本，則會使用該版本的最新已安裝 SDK **修補程式版本**。</span><span class="sxs-lookup"><span data-stu-id="a9def-135">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="a9def-136">最新已安裝的 SDK **修補程式版本**可以是發行版本或發行前版本，而最高版本號碼優先採用。</span><span class="sxs-lookup"><span data-stu-id="a9def-136">Latest installed SDK **patch version** can be either release or pre-release - the highest version number wins.</span></span> <span data-ttu-id="a9def-137">對於 .NET Core 2.1 和更新版本，在 SDK 選取項目中，低於指定的**修補程式版本**的**修補程式版本**會被忽略。</span><span class="sxs-lookup"><span data-stu-id="a9def-137">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="a9def-138">如果找不到指定的 SDK 版本和適當的 SDK **修補程式版本**，則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="a9def-138">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="a9def-139">SDK 版本目前由下列部分組成：</span><span class="sxs-lookup"><span data-stu-id="a9def-139">The SDK version is currently composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="a9def-140">.NET Core SDK **功能版本**是由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的第一個數字 (`x`) 表示。</span><span class="sxs-lookup"><span data-stu-id="a9def-140">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="a9def-141">一般而言，.NET Core SDK 的發行週期比 .NET Core 快。</span><span class="sxs-lookup"><span data-stu-id="a9def-141">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="a9def-142">**修補程式版本**由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的最後兩個數字 (`yz`) 定義。</span><span class="sxs-lookup"><span data-stu-id="a9def-142">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="a9def-143">例如，如果指定 `2.1.300` 做為 SDK 版本，SDK 選取項目最高會找到 `2.1.399`，但是 `2.1.400` 不視為 `2.1.300` 的修補版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-143">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="a9def-144">.NET Core SDK 版本 `2.1.100` 到 `2.1.201` 是在版本號碼轉換期間發行，它們並沒有正確地處理 `xyz` 標記法。</span><span class="sxs-lookup"><span data-stu-id="a9def-144">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="a9def-145">強烈建議如果您在 *global.json* 檔案中指定這些版本，則必須確保目標電腦上有這些指定的版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-145">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

<span data-ttu-id="a9def-146">對於.NET Core SDK 1.x，如果您指定了某個版本但找不到它，則會使用最新安裝的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-146">With .NET Core SDK 1.x, if you specified a version and no exact match was found, the latest installed SDK version was used.</span></span> <span data-ttu-id="a9def-147">最新的 SDK 版本可以是發行版本或發行前版本，而最高版本號碼優先採用。</span><span class="sxs-lookup"><span data-stu-id="a9def-147">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="a9def-148">為組建警告進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="a9def-148">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="a9def-149">您正在使用.NET Core SDK 的預覽版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-149">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="a9def-150">您可以在目前的專案中透過 global.json 檔案定義 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-150">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="a9def-151">詳情請見 <https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="a9def-151">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="a9def-152">這則警告指出您的專案正使用.NET Core SDK 的預覽版本編譯，如[比對規則](#matching-rules)一節中的說明。</span><span class="sxs-lookup"><span data-stu-id="a9def-152">This warning indicates that your project is being compiled using a preview version of the .NET Core SDK, as explained in the [Matching rules](#matching-rules) section.</span></span> <span data-ttu-id="a9def-153">.NET Core SDK 版本一向承諾提供高品質的產品。</span><span class="sxs-lookup"><span data-stu-id="a9def-153">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="a9def-154">不過，如果您不想使用預覽版本，請新增 *global.json* 檔案到專案階層架構以指定要使用的 SDK 版本，並使用 `dotnet --list-sdks` 來確認電腦上已安裝該版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-154">However, if you don't want to use a preview version, add a *global.json* file to your project hierarchy structure to specify which SDK version to use, and use `dotnet --list-sdks` to confirm that the version is installed on your machine.</span></span> <span data-ttu-id="a9def-155">新版本發行時，若要使用新的版本，可移除 *global.json* 檔案或更新它以使用較新版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-155">When a new version is released, to use the new version, either remove the *global.json* file or update it to use the newer version.</span></span>

> [!WARNING]
> <span data-ttu-id="a9def-156">啟動專案 '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'。</span><span class="sxs-lookup"><span data-stu-id="a9def-156">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="a9def-157">這個版本的 Entity Framework Core.NET 命令列工具僅支援 2.0 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-157">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="a9def-158">如需使用較舊版本工具的詳細資訊，請參閱 <https://go.microsoft.com/fwlink/?linkid=871254> \(英文\)</span><span class="sxs-lookup"><span data-stu-id="a9def-158">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="a9def-159">從 .NET Core 2.1 SDK (2.1.300 版) 開始，`dotnet ef` 命令會包含在 SDK 中。</span><span class="sxs-lookup"><span data-stu-id="a9def-159">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="a9def-160">這個警告指出您的專案目標為 EF Core 1.0 或 1.1，與 .NET Core 2.1 SDK 和更新版本不相容。</span><span class="sxs-lookup"><span data-stu-id="a9def-160">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions.</span></span> <span data-ttu-id="a9def-161">若要編譯您的專案，請在您的機器上安裝 .NET Core 2.0 SDK (2.1.201 版) 和更舊版本，然後使用 *global.json* 檔案來定義所需的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="a9def-161">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="a9def-162">如需 `dotnet ef` 命令的詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="a9def-162">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9def-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9def-163">See also</span></span>

- [<span data-ttu-id="a9def-164">解析專案 SDK 的方式</span><span class="sxs-lookup"><span data-stu-id="a9def-164">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)