---
title: global.json 概觀
description: 了解如何使用 global.json 檔案來設定執行.NET Core CLI 命令時的 NET Core SDK 版本。
ms.date: 04/21/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5384b59cccb629a5409d26a8df7c81b3999fc95f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021345"
---
# <a name="globaljson-overview"></a><span data-ttu-id="4091a-103">global.json 概觀</span><span class="sxs-lookup"><span data-stu-id="4091a-103">global.json overview</span></span>

<span data-ttu-id="4091a-104">**本文適用於:✔️** .NET Core 2.0 SDK 和更高版本</span><span class="sxs-lookup"><span data-stu-id="4091a-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="4091a-105">*global.json* 檔案可讓您定義執行.NET Core CLI 命令時所使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="4091a-106">選取 .NET Core SDK 與指定專案所針對的執行階段沒有關係。</span><span class="sxs-lookup"><span data-stu-id="4091a-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="4091a-107">.NET 核心 SDK 版本指示使用了 .NET 核心 CLI 的哪些版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="4091a-108">通常,您希望使用最新版本的 SDK 工具,因此不需要*全域.json*檔。</span><span class="sxs-lookup"><span data-stu-id="4091a-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="4091a-109">在某些高級方案中,您可能希望控制 SDK 工具的版本,本文將介紹如何執行此操作。</span><span class="sxs-lookup"><span data-stu-id="4091a-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="4091a-110">如需改為指定執行階段的詳細資訊，請參閱[目標架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="4091a-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="4091a-111">.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找 *global.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="4091a-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="4091a-112">global.json 結構描述</span><span class="sxs-lookup"><span data-stu-id="4091a-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="4091a-113">sdk</span><span class="sxs-lookup"><span data-stu-id="4091a-113">sdk</span></span>

<span data-ttu-id="4091a-114">輸入： `object`</span><span class="sxs-lookup"><span data-stu-id="4091a-114">Type: `object`</span></span>

<span data-ttu-id="4091a-115">指定要選取 .NET Core SDK 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4091a-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="4091a-116">version</span><span class="sxs-lookup"><span data-stu-id="4091a-116">version</span></span>

- <span data-ttu-id="4091a-117">輸入： `string`</span><span class="sxs-lookup"><span data-stu-id="4091a-117">Type: `string`</span></span>

- <span data-ttu-id="4091a-118">自: .NET 核心 1.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="4091a-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="4091a-119">要使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="4091a-120">此欄位:</span><span class="sxs-lookup"><span data-stu-id="4091a-120">This field:</span></span>

- <span data-ttu-id="4091a-121">沒有通配符支援,也就是說,必須指定完整版本號。</span><span class="sxs-lookup"><span data-stu-id="4091a-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="4091a-122">不支援版本範圍。</span><span class="sxs-lookup"><span data-stu-id="4091a-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="4091a-123">允許預釋放</span><span class="sxs-lookup"><span data-stu-id="4091a-123">allowPrerelease</span></span>

- <span data-ttu-id="4091a-124">輸入： `boolean`</span><span class="sxs-lookup"><span data-stu-id="4091a-124">Type: `boolean`</span></span>

- <span data-ttu-id="4091a-125">自: .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="4091a-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="4091a-126">指示 SDK 解析器在選擇要使用的 SDK 版本時是否應考慮預發佈版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="4091a-127">如果未顯示式設定這個值,則預設值取決於您是否從 Visual Studio 執行:</span><span class="sxs-lookup"><span data-stu-id="4091a-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="4091a-128">如果您**不在**Visual Studio 中,則`true`預設值為 。</span><span class="sxs-lookup"><span data-stu-id="4091a-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="4091a-129">如果您在 Visual Studio 中,它將使用請求的預先發佈狀態。</span><span class="sxs-lookup"><span data-stu-id="4091a-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="4091a-130">也就是說,如果您使用的是 Visual Studio 的預覽版,或者設置了 **.NET 核心 SDK 選項的「使用預覽**」(在`true`**「工具** > **選項** > **環境** > **預覽功能**」下 ),則預設值為 ;否則, `false`.</span><span class="sxs-lookup"><span data-stu-id="4091a-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="4091a-131">捲軸</span><span class="sxs-lookup"><span data-stu-id="4091a-131">rollForward</span></span>

- <span data-ttu-id="4091a-132">輸入： `string`</span><span class="sxs-lookup"><span data-stu-id="4091a-132">Type: `string`</span></span>

- <span data-ttu-id="4091a-133">自: .NET 核心 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="4091a-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="4091a-134">選擇 SDK 版本時使用的滾前策略,在缺少特定 SDK 版本時作為回退策略,也可以用作使用更高版本的指令。</span><span class="sxs-lookup"><span data-stu-id="4091a-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="4091a-135">必須[version](#version)使用`rollForward`值指定版本,除非您將其設定為`latestMajor`。</span><span class="sxs-lookup"><span data-stu-id="4091a-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="4091a-136">要瞭解可用的策略及其行為,請考慮以下格式`x.y.znn`為 SDK 版本的定義:</span><span class="sxs-lookup"><span data-stu-id="4091a-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="4091a-137">`x`是主要版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-137">`x` is the major version.</span></span>
- <span data-ttu-id="4091a-138">`y`是次要版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-138">`y` is the minor version.</span></span>
- <span data-ttu-id="4091a-139">`z`是要素帶。</span><span class="sxs-lookup"><span data-stu-id="4091a-139">`z` is the feature band.</span></span>
- <span data-ttu-id="4091a-140">`nn`是補丁版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-140">`nn` is the patch version.</span></span>

<span data-ttu-id="4091a-141">下表顯示了金鑰的可能`rollForward`值:</span><span class="sxs-lookup"><span data-stu-id="4091a-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="4091a-142">值</span><span class="sxs-lookup"><span data-stu-id="4091a-142">Value</span></span>         | <span data-ttu-id="4091a-143">行為</span><span class="sxs-lookup"><span data-stu-id="4091a-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="4091a-144">使用指定的版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-144">Uses the specified version.</span></span> <br> <span data-ttu-id="4091a-145">如果未找到,則向前滾動到最新的修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="4091a-146">如果未找到,則失敗。</span><span class="sxs-lookup"><span data-stu-id="4091a-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="4091a-147">此值是 SDK 早期版本中的舊行為。</span><span class="sxs-lookup"><span data-stu-id="4091a-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="4091a-148">對指定的主波段、次要波段和功能波段使用最新的修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="4091a-149">如果未找到,則向前滾動到同一主/次要中的下一個較高要素波段,併為該要素波段使用最新的修補程式級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="4091a-150">如果未找到,則失敗。</span><span class="sxs-lookup"><span data-stu-id="4091a-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="4091a-151">對指定的主波段、次要波段和功能波段使用最新的修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="4091a-152">如果未找到,則在同一主/次要版本中向前滾動到下一個更高的要素波段,併為該功能波段使用最新的修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="4091a-153">如果未找到,則向前滾動到同一主區中的下一個較高的次要和功能波段,併為此要素波段使用最新的修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="4091a-154">如果未找到,則失敗。</span><span class="sxs-lookup"><span data-stu-id="4091a-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="4091a-155">對指定的主波段、次要波段和功能波段使用最新的修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="4091a-156">如果未找到,則在同一主/次要版本中向前滾動到下一個更高的要素波段,併為該功能波段使用最新的修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="4091a-157">如果未找到,則向前滾動到同一主區中的下一個較高的次要和功能波段,併為此要素波段使用最新的修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="4091a-158">如果未找到,則向前滾動到下一個更高的主、次要和功能波段,並使用該功能波段的最新修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="4091a-159">如果未找到,則失敗。</span><span class="sxs-lookup"><span data-stu-id="4091a-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="4091a-160">使用與修補程式級別匹配請求的主要、次要和功能帶且大於或等於指定值的最新已安裝修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="4091a-161">如果未找到,則失敗。</span><span class="sxs-lookup"><span data-stu-id="4091a-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="4091a-162">使用與請求的主要和次要要素帶匹配的最高安裝功能帶和修補程式級別,要素帶大於或等於指定值。</span><span class="sxs-lookup"><span data-stu-id="4091a-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="4091a-163">如果未找到,則失敗。</span><span class="sxs-lookup"><span data-stu-id="4091a-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="4091a-164">使用與請求的主要要素與大於或等於指定值的次要匹配的最高安裝次要、功能帶和修補程序級別。</span><span class="sxs-lookup"><span data-stu-id="4091a-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="4091a-165">如果未找到,則失敗。</span><span class="sxs-lookup"><span data-stu-id="4091a-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="4091a-166">使用安裝量最高的 .NET Core SDK,其主版本大於或等於指定值。</span><span class="sxs-lookup"><span data-stu-id="4091a-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="4091a-167">如果未找到,則失敗。</span><span class="sxs-lookup"><span data-stu-id="4091a-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="4091a-168">不會向前滾動。</span><span class="sxs-lookup"><span data-stu-id="4091a-168">Doesn't roll forward.</span></span> <span data-ttu-id="4091a-169">需要完全匹配。</span><span class="sxs-lookup"><span data-stu-id="4091a-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="4091a-170">範例</span><span class="sxs-lookup"><span data-stu-id="4091a-170">Examples</span></span>

<span data-ttu-id="4091a-171">下面的範例展示如何不使用預發行版本:</span><span class="sxs-lookup"><span data-stu-id="4091a-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="4091a-172">下面的範例展示如何使用安裝的大於或等於指定版本的最高版本:</span><span class="sxs-lookup"><span data-stu-id="4091a-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="4091a-173">下面的範例展示如何使用指定的精確版本:</span><span class="sxs-lookup"><span data-stu-id="4091a-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="4091a-174">下面的範例展示如何使用特定主要版本和次要版本安裝的最新功能波段和修補程式版本:</span><span class="sxs-lookup"><span data-stu-id="4091a-174">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.000",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="4091a-175">下面的範例展示如何使用特定版本安裝的最高修補程式版本(在窗體中,3.1.1xx):</span><span class="sxs-lookup"><span data-stu-id="4091a-175">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="4091a-176">global.json 和.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="4091a-176">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="4091a-177">瞭解電腦上安裝了哪些 SDK 版本以在*global.json*檔中設置一個 SDK 版本會很有説明。</span><span class="sxs-lookup"><span data-stu-id="4091a-177">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="4091a-178">有關如何執行此操作的詳細資訊,請參閱[如何檢查 .NET Core 是否已安裝](../install/how-to-detect-installed-versions.md#check-sdk-versions)。</span><span class="sxs-lookup"><span data-stu-id="4091a-178">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="4091a-179">要在電腦上安裝其他 .NET 核心 SDK 版本,請造訪[下載 .NET 核心](https://dotnet.microsoft.com/download/dotnet-core)頁面。</span><span class="sxs-lookup"><span data-stu-id="4091a-179">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="4091a-180">執行 [dotnet new](dotnet-new.md) 命令，可在目前的目錄中建立新的 *global.json* 檔案，與下面的範例類似：</span><span class="sxs-lookup"><span data-stu-id="4091a-180">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="4091a-181">比對規則</span><span class="sxs-lookup"><span data-stu-id="4091a-181">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="4091a-182">匹配規則由`dotnet.exe`入口點控制,該入口點在所有已安裝的 .NET Core 安裝運行時中很常見。</span><span class="sxs-lookup"><span data-stu-id="4091a-182">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="4091a-183">當您並排安裝多個運行時時,將使用 .NET Core 運行時最新安裝版本的匹配規則。</span><span class="sxs-lookup"><span data-stu-id="4091a-183">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="4091a-184">.NET Core 3.x</span><span class="sxs-lookup"><span data-stu-id="4091a-184">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="4091a-185">從 .NET Core 3.0 開始,在確定要使用的 SDK 版本時,適用以下規則:</span><span class="sxs-lookup"><span data-stu-id="4091a-185">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="4091a-186">如果未找到*global.json*檔,或者*global.json*未指定`allowPrerelease`SDK 版本或 值,則使用安裝最高的`rollForward`SDK 版本(等效於 設置為`latestMajor`)。</span><span class="sxs-lookup"><span data-stu-id="4091a-186">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="4091a-187">是否考慮預先發佈 SDK`dotnet`版本取決於如何 呼叫。</span><span class="sxs-lookup"><span data-stu-id="4091a-187">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="4091a-188">如果您**不在**Visual Studio 中,則會考慮預發佈版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-188">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="4091a-189">如果您在 Visual Studio 中,它將使用請求的預先發佈狀態。</span><span class="sxs-lookup"><span data-stu-id="4091a-189">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="4091a-190">也就是說,如果您使用的是 Visual Studio 的預覽版,或者設置了 **.NET 核心 SDK 選項的「使用預覽**」(在 **「工具** > **選項** > **環境** > **預覽功能**」下),則考慮預先發佈版本;否則,僅考慮發佈版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-190">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="4091a-191">如果發現*global.json*檔不指定 SDK 版本,`allowPrerelease`但它指定值 ,則使用安裝最高的 SDK`rollForward``latestMajor`版本(等效於設置為 )。</span><span class="sxs-lookup"><span data-stu-id="4091a-191">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="4091a-192">最新的 SDK 版本是否可以發布或預先發佈`allowPrerelease`的值 。</span><span class="sxs-lookup"><span data-stu-id="4091a-192">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="4091a-193">`true`指示考慮預發行版本;`false`表示只考慮發佈版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-193">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="4091a-194">找不到*global.json*檔並指定 SDK 版本:</span><span class="sxs-lookup"><span data-stu-id="4091a-194">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="4091a-195">如果未`rollFoward`設置任何值,則用作`latestPatch``rollForward`預設策略。</span><span class="sxs-lookup"><span data-stu-id="4091a-195">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="4091a-196">否則,請在[「滾動前進」](#rollforward)部分中檢查每個值及其行為。</span><span class="sxs-lookup"><span data-stu-id="4091a-196">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="4091a-197">是否考慮預發佈版本以及未設置時的`allowPrerelease`默認行為在[「允許預發佈](#allowprerelease)」部分中介紹。</span><span class="sxs-lookup"><span data-stu-id="4091a-197">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="4091a-198">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4091a-198">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="4091a-199">在 .NET Core 2.x SDK 中,在確定要使用的 SDK 版本時,適用以下規則:</span><span class="sxs-lookup"><span data-stu-id="4091a-199">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="4091a-200">如果找不到 *global.json* 檔案或 *global.json* 沒有指定 SDK 版本，則會使用最新安裝的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-200">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="4091a-201">最新的 SDK 版本可以是發佈版本或預發佈 - 最高版本號獲勝。</span><span class="sxs-lookup"><span data-stu-id="4091a-201">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="4091a-202">如果 *global.json* 未指定 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="4091a-202">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="4091a-203">如果在電腦上找到了指定的 SDK 版本，則會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-203">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="4091a-204">如果在電腦上找不到指定的 SDK 版本，則會使用該版本的最新已安裝 SDK **修補程式版本**。</span><span class="sxs-lookup"><span data-stu-id="4091a-204">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="4091a-205">最新安裝的 SDK**修補程式版本**可以是發佈版本或預發佈 - 最高版本號獲勝。</span><span class="sxs-lookup"><span data-stu-id="4091a-205">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="4091a-206">對於 .NET Core 2.1 和更新版本，在 SDK 選取項目中，低於指定的**修補程式版本**的**修補程式版本**會被忽略。</span><span class="sxs-lookup"><span data-stu-id="4091a-206">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="4091a-207">如果找不到指定的 SDK 版本和適當的 SDK **修補程式版本**，則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="4091a-207">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="4091a-208">SDK 版本由以下部份組成:</span><span class="sxs-lookup"><span data-stu-id="4091a-208">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="4091a-209">.NET Core SDK **功能版本**是由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的第一個數字 (`x`) 表示。</span><span class="sxs-lookup"><span data-stu-id="4091a-209">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="4091a-210">一般而言，.NET Core SDK 的發行週期比 .NET Core 快。</span><span class="sxs-lookup"><span data-stu-id="4091a-210">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="4091a-211">**修補程式版本**由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的最後兩個數字 (`yz`) 定義。</span><span class="sxs-lookup"><span data-stu-id="4091a-211">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="4091a-212">例如，如果指定 `2.1.300` 做為 SDK 版本，SDK 選取項目最高會找到 `2.1.399`，但是 `2.1.400` 不視為 `2.1.300` 的修補版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-212">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="4091a-213">.NET Core SDK 版本 `2.1.100` 到 `2.1.201` 是在版本號碼轉換期間發行，它們並沒有正確地處理 `xyz` 標記法。</span><span class="sxs-lookup"><span data-stu-id="4091a-213">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="4091a-214">強烈建議如果您在 *global.json* 檔案中指定這些版本，則必須確保目標電腦上有這些指定的版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-214">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="4091a-215">排除產生警告</span><span class="sxs-lookup"><span data-stu-id="4091a-215">Troubleshoot build warnings</span></span>

* <span data-ttu-id="4091a-216">以下警告指示您的項目是使用 .NET Core SDK 的預先發佈版本編譯的:</span><span class="sxs-lookup"><span data-stu-id="4091a-216">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="4091a-217">您正在使用.NET Core SDK 的預覽版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-217">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="4091a-218">您可以在目前的專案中透過 global.json 檔案定義 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-218">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="4091a-219">更多在<https://go.microsoft.com/fwlink/?linkid=869452>。</span><span class="sxs-lookup"><span data-stu-id="4091a-219">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="4091a-220">.NET Core SDK 版本一向承諾提供高品質的產品。</span><span class="sxs-lookup"><span data-stu-id="4091a-220">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="4091a-221">但是,如果您不想使用預先發佈版本,請檢查可在允許[預先發佈](#allowprerelease)部分中使用 .NET Core 3.0 SDK 或更高版本的不同策略。</span><span class="sxs-lookup"><span data-stu-id="4091a-221">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="4091a-222">對於從未安裝過 .NET Core 3.0 或更高執行時或 SDK 的電腦,您需要創建*全域.json*檔並指定要使用的確切版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-222">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="4091a-223">以下警告指示您的項目以 EF Core 1.0 或 1.1 為目標,後者與 .NET Core 2.1 SDK 和更高版本不相容:</span><span class="sxs-lookup"><span data-stu-id="4091a-223">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="4091a-224">啟動專案 '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'。</span><span class="sxs-lookup"><span data-stu-id="4091a-224">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="4091a-225">這個版本的 Entity Framework Core.NET 命令列工具僅支援 2.0 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-225">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="4091a-226">有關使用舊版本的工具的資訊,請參<https://go.microsoft.com/fwlink/?linkid=871254>閱 。</span><span class="sxs-lookup"><span data-stu-id="4091a-226">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="4091a-227">從 .NET Core 2.1 SDK (2.1.300 版) 開始，`dotnet ef` 命令會包含在 SDK 中。</span><span class="sxs-lookup"><span data-stu-id="4091a-227">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="4091a-228">要編譯專案,請在電腦上安裝 .NET Core 2.0 SDK(版本 2.1.201)或更早版本,並使用*global.json*檔定義所需的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="4091a-228">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="4091a-229">如需 `dotnet ef` 命令的詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="4091a-229">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="4091a-230">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4091a-230">See also</span></span>

- [<span data-ttu-id="4091a-231">解析專案 SDK 的方式</span><span class="sxs-lookup"><span data-stu-id="4091a-231">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
