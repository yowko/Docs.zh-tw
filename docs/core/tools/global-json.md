---
title: global.json 概觀
description: 了解如何使用 global.json 檔案來設定執行.NET Core CLI 命令時的 NET Core SDK 版本。
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a9558090b1ef48f376334fbc826f6265a58908da
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062791"
---
# <a name="globaljson-overview"></a><span data-ttu-id="9ab95-103">global.json 概觀</span><span class="sxs-lookup"><span data-stu-id="9ab95-103">global.json overview</span></span>

<span data-ttu-id="9ab95-104">**本文適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="9ab95-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="9ab95-105">*global.json* 檔案可讓您定義執行.NET Core CLI 命令時所使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="9ab95-106">選取 .NET Core SDK 與指定專案所針對的執行階段沒有關係。</span><span class="sxs-lookup"><span data-stu-id="9ab95-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="9ab95-107">.NET Core SDK 版本指出所使用的 .NET Core CLI 版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="9ab95-108">一般來說，您會想要使用最新版的 SDK 工具，因此不需要*global.js*檔案。</span><span class="sxs-lookup"><span data-stu-id="9ab95-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="9ab95-109">在某些先進的案例中，您可能會想要控制 SDK 工具的版本，這篇文章會說明如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="9ab95-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="9ab95-110">如需改為指定執行階段的詳細資訊，請參閱[目標架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab95-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="9ab95-111">.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找 *global.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="9ab95-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="9ab95-112">global.json 結構描述</span><span class="sxs-lookup"><span data-stu-id="9ab95-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="9ab95-113">sdk</span><span class="sxs-lookup"><span data-stu-id="9ab95-113">sdk</span></span>

<span data-ttu-id="9ab95-114">輸入： `object`</span><span class="sxs-lookup"><span data-stu-id="9ab95-114">Type: `object`</span></span>

<span data-ttu-id="9ab95-115">指定要選取 .NET Core SDK 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9ab95-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="9ab95-116">version</span><span class="sxs-lookup"><span data-stu-id="9ab95-116">version</span></span>

- <span data-ttu-id="9ab95-117">輸入： `string`</span><span class="sxs-lookup"><span data-stu-id="9ab95-117">Type: `string`</span></span>

- <span data-ttu-id="9ab95-118">自： .NET Core 1.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ab95-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="9ab95-119">要使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="9ab95-120">此欄位：</span><span class="sxs-lookup"><span data-stu-id="9ab95-120">This field:</span></span>

- <span data-ttu-id="9ab95-121">不支援萬用字元，也就是必須指定完整的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="9ab95-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="9ab95-122">不支援版本範圍。</span><span class="sxs-lookup"><span data-stu-id="9ab95-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="9ab95-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="9ab95-123">allowPrerelease</span></span>

- <span data-ttu-id="9ab95-124">輸入： `boolean`</span><span class="sxs-lookup"><span data-stu-id="9ab95-124">Type: `boolean`</span></span>

- <span data-ttu-id="9ab95-125">自： .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ab95-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="9ab95-126">指出當選取要使用的 SDK 版本時，SDK 解析程式是否應考慮發行前版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="9ab95-127">如果您未明確設定此值，則預設值取決於您是否從 Visual Studio 執行：</span><span class="sxs-lookup"><span data-stu-id="9ab95-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="9ab95-128">如果您**不**是 Visual Studio，預設值是 `true` 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="9ab95-129">如果您處於 Visual Studio，則會使用所要求的發行前版本狀態。</span><span class="sxs-lookup"><span data-stu-id="9ab95-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="9ab95-130">也就是說，如果您使用 Visual Studio 的預覽版本，或在 [**工具**] [選項] [環境] [預覽功能]) 底下設定 [**使用 .NET Core SDK** (選項的預覽]  >  **Options**  >  **Environment**  >  **Preview Features** ，則預設值為 `true` ; 否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="9ab95-131">向前復原</span><span class="sxs-lookup"><span data-stu-id="9ab95-131">rollForward</span></span>

- <span data-ttu-id="9ab95-132">輸入： `string`</span><span class="sxs-lookup"><span data-stu-id="9ab95-132">Type: `string`</span></span>

- <span data-ttu-id="9ab95-133">自： .NET Core 3.0 SDK 起提供。</span><span class="sxs-lookup"><span data-stu-id="9ab95-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="9ab95-134">選取 SDK 版本時要使用的向前復原原則，可以在特定 SDK 版本遺失時做為回溯，或做為使用較高版本的指示詞。</span><span class="sxs-lookup"><span data-stu-id="9ab95-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="9ab95-135">[version](#version) `rollForward` 除非您要將其設定為，否則必須使用值來指定版本 `latestMajor` 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="9ab95-136">若要瞭解可用的原則及其行為，請考慮下列格式的 SDK 版本定義 `x.y.znn` ：</span><span class="sxs-lookup"><span data-stu-id="9ab95-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="9ab95-137">`x`是主要版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-137">`x` is the major version.</span></span>
- <span data-ttu-id="9ab95-138">`y`是次要版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-138">`y` is the minor version.</span></span>
- <span data-ttu-id="9ab95-139">`z`是功能區。</span><span class="sxs-lookup"><span data-stu-id="9ab95-139">`z` is the feature band.</span></span>
- <span data-ttu-id="9ab95-140">`nn`是修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-140">`nn` is the patch version.</span></span>

<span data-ttu-id="9ab95-141">下表顯示索引鍵的可能值 `rollForward` ：</span><span class="sxs-lookup"><span data-stu-id="9ab95-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="9ab95-142">值</span><span class="sxs-lookup"><span data-stu-id="9ab95-142">Value</span></span>         | <span data-ttu-id="9ab95-143">行為</span><span class="sxs-lookup"><span data-stu-id="9ab95-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="9ab95-144">使用指定的版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-144">Uses the specified version.</span></span> <br> <span data-ttu-id="9ab95-145">如果找不到，則會向前復原到最新的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="9ab95-146">如果找不到，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ab95-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="9ab95-147">這個值是舊版 SDK 的舊行為。</span><span class="sxs-lookup"><span data-stu-id="9ab95-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="9ab95-148">會針對指定的主要、次要和功能區使用最新的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="9ab95-149">如果找不到，則會向前復原至相同主要/次要內的下一個較高功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="9ab95-150">如果找不到，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ab95-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="9ab95-151">會針對指定的主要、次要和功能區使用最新的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="9ab95-152">如果找不到，則會向前復原至相同主要/次要版本內的下一個較高功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="9ab95-153">如果找不到，則會向前復原至相同主要的下一個較高次要和功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="9ab95-154">如果找不到，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ab95-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="9ab95-155">會針對指定的主要、次要和功能區使用最新的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="9ab95-156">如果找不到，則會向前復原至相同主要/次要版本內的下一個較高功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="9ab95-157">如果找不到，則會向前復原至相同主要的下一個較高次要和功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="9ab95-158">如果找不到，則會向前復原至下一個較高的主要、次要和功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="9ab95-159">如果找不到，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ab95-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="9ab95-160">會使用符合所要求之主要、次要和功能區的最新已安裝修補程式等級，且其修補程式等級大於或等於指定的值。</span><span class="sxs-lookup"><span data-stu-id="9ab95-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="9ab95-161">如果找不到，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ab95-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="9ab95-162">使用的最高安裝功能區和修補程式等級，符合所要求的主要和次要，以及大於或等於指定值的功能區。</span><span class="sxs-lookup"><span data-stu-id="9ab95-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="9ab95-163">如果找不到，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ab95-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="9ab95-164">會使用最高安裝的次要、功能區，以及符合所要求主要的次要、大於或等於指定值的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="9ab95-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="9ab95-165">如果找不到，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ab95-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="9ab95-166">使用已安裝的最高 .NET Core SDK，其主要大於或等於指定的值。</span><span class="sxs-lookup"><span data-stu-id="9ab95-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="9ab95-167">如果找不到，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="9ab95-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="9ab95-168">不向前復原。</span><span class="sxs-lookup"><span data-stu-id="9ab95-168">Doesn't roll forward.</span></span> <span data-ttu-id="9ab95-169">需要完全相符。</span><span class="sxs-lookup"><span data-stu-id="9ab95-169">Exact match required.</span></span> |

### <a name="msbuild-sdks"></a><span data-ttu-id="9ab95-170">msbuild-sdk</span><span class="sxs-lookup"><span data-stu-id="9ab95-170">msbuild-sdks</span></span>

<span data-ttu-id="9ab95-171">輸入： `object`</span><span class="sxs-lookup"><span data-stu-id="9ab95-171">Type: `object`</span></span>

<span data-ttu-id="9ab95-172">可讓您在一個位置控制專案 SDK 版本，而不是在每個個別專案中。</span><span class="sxs-lookup"><span data-stu-id="9ab95-172">Lets you control the project SDK version in one place rather than in each individual project.</span></span> <span data-ttu-id="9ab95-173">如需詳細資訊，請參閱[專案 sdk 的解析方式](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)。</span><span class="sxs-lookup"><span data-stu-id="9ab95-173">For more information, see [How project SDKs are resolved](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span></span>

## <a name="examples"></a><span data-ttu-id="9ab95-174">範例</span><span class="sxs-lookup"><span data-stu-id="9ab95-174">Examples</span></span>

<span data-ttu-id="9ab95-175">下列範例顯示如何不使用發行前版本：</span><span class="sxs-lookup"><span data-stu-id="9ab95-175">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="9ab95-176">下列範例顯示如何使用安裝的最高版本（大於或等於指定的版本）。</span><span class="sxs-lookup"><span data-stu-id="9ab95-176">The following example shows how to use the highest version installed that is greater or equal than the specified version.</span></span> <span data-ttu-id="9ab95-177">所顯示的 JSON 不允許任何早于2.2.200 的 SDK 版本，並允許2.2.200 或任何較新版本，包括3.0.xxx 和3.1.xxx。</span><span class="sxs-lookup"><span data-stu-id="9ab95-177">The JSON shown disallows any SDK version earlier than 2.2.200 and allows 2.2.200 or any later version, including 3.0.xxx and 3.1.xxx.</span></span>

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="9ab95-178">下列範例顯示如何使用正確的指定版本：</span><span class="sxs-lookup"><span data-stu-id="9ab95-178">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="9ab95-179">下列範例示範如何使用安裝在特定主要和次要版本的最新功能區和修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-179">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version.</span></span> <span data-ttu-id="9ab95-180">所顯示的 JSON 不允許任何早于3.1.102 的 SDK 版本，並允許3.1.102 或任何較新的3.1.xxx 版本，例如3.1.103 或3.1.200。</span><span class="sxs-lookup"><span data-stu-id="9ab95-180">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.xxx version, such as 3.1.103 or 3.1.200.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="9ab95-181">下列範例顯示如何使用已安裝的特定版本最高的修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-181">The following example shows how to use the highest patch version installed of a specific version.</span></span> <span data-ttu-id="9ab95-182">所顯示的 JSON 不允許任何早于3.1.102 的 SDK 版本，並允許3.1.102 或任何較新的 3.1.1 xx 版本，例如3.1.103 或3.1.199。</span><span class="sxs-lookup"><span data-stu-id="9ab95-182">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.1xx version, such as 3.1.103 or 3.1.199.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="9ab95-183">global.json 和.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="9ab95-183">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="9ab95-184">瞭解哪些 SDK 版本已安裝在您的電腦上，以在檔案的*global.js*中設定一個，會很有説明。</span><span class="sxs-lookup"><span data-stu-id="9ab95-184">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="9ab95-185">如需如何執行此動作的詳細資訊，請參閱[如何檢查是否已安裝 .Net Core](../install/how-to-detect-installed-versions.md#check-sdk-versions)。</span><span class="sxs-lookup"><span data-stu-id="9ab95-185">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="9ab95-186">若要在您的電腦上安裝其他 .NET Core SDK 版本，請造訪[下載 .Net Core](https://dotnet.microsoft.com/download/dotnet-core)頁面。</span><span class="sxs-lookup"><span data-stu-id="9ab95-186">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="9ab95-187">執行 [dotnet new](dotnet-new.md) 命令，可在目前的目錄中建立新的 *global.json* 檔案，與下面的範例類似：</span><span class="sxs-lookup"><span data-stu-id="9ab95-187">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="9ab95-188">比對規則</span><span class="sxs-lookup"><span data-stu-id="9ab95-188">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="9ab95-189">比對規則是由進入點所控管 `dotnet.exe` ，這在所有已安裝的 .Net Core 安裝執行時間中都是通用的。</span><span class="sxs-lookup"><span data-stu-id="9ab95-189">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="9ab95-190">當您有多個並行安裝的執行時間時，會使用 .NET Core 執行時間最新安裝版本的比對規則。</span><span class="sxs-lookup"><span data-stu-id="9ab95-190">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="9ab95-191">.NET Core 3.x</span><span class="sxs-lookup"><span data-stu-id="9ab95-191">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="9ab95-192">從 .NET Core 3.0 開始，判斷要使用的 SDK 版本時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="9ab95-192">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="9ab95-193">如果找不到檔案的*global.js* ，或*上的global.js*未指定 SDK 版本或 `allowPrerelease` 值，則會使用最高的已安裝 SDK 版本 (相當於設定 `rollForward` 為 [) ] `latestMajor` 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-193">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="9ab95-194">是否要考慮發行前版本 SDK，取決於叫用的方式 `dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-194">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="9ab95-195">如果您**不**是 Visual Studio，則會考慮發行前版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-195">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="9ab95-196">如果您處於 Visual Studio，則會使用所要求的發行前版本狀態。</span><span class="sxs-lookup"><span data-stu-id="9ab95-196">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="9ab95-197">也就是說，如果您使用 Visual Studio 的預覽版本，或在 [**工具**] [選項] [環境] [預覽) 功能] 下設定 [**使用 .NET Core SDK**選項的預覽] ( >  **Options**  >  **Environment**  >  **Preview Features** ，則會考慮發行前版本，否則只會考慮發行版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-197">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="9ab95-198">如果找到的*global.js*檔案未指定 SDK 版本，但指定了 `allowPrerelease` 值，則會使用最高安裝的 sdk 版本， (相當於將設定 `rollForward` 為 [) ] `latestMajor` 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-198">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="9ab95-199">最新的 SDK 版本是否可以發行或發行前版本，取決於的值 `allowPrerelease` 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-199">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="9ab95-200">`true`表示已考慮發行前版本;`false`指出只會考慮發行版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-200">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="9ab95-201">如果找到檔案*上的global.js* ，而且它指定 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="9ab95-201">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="9ab95-202">如果未 `rollFoward` 設定任何值，則會使用 `latestPatch` 做為預設 `rollForward` 原則。</span><span class="sxs-lookup"><span data-stu-id="9ab95-202">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="9ab95-203">否則，請檢查[向前復原](#rollforward)區段中的每個值及其行為。</span><span class="sxs-lookup"><span data-stu-id="9ab95-203">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="9ab95-204">是否考慮發行前版本，以及未設定時的預設行為，請 `allowPrerelease` 參閱[allowPrerelease](#allowprerelease)一節。</span><span class="sxs-lookup"><span data-stu-id="9ab95-204">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="9ab95-205">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="9ab95-205">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="9ab95-206">在 .NET Core 2.x SDK 中，當您決定要使用的 SDK 版本時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="9ab95-206">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="9ab95-207">如果找不到 *global.json* 檔案或 *global.json* 沒有指定 SDK 版本，則會使用最新安裝的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-207">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="9ab95-208">最新的 SDK 版本可以是發行版本或發行前版本，最高的版本號碼獲勝。</span><span class="sxs-lookup"><span data-stu-id="9ab95-208">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="9ab95-209">如果 *global.json* 未指定 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="9ab95-209">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="9ab95-210">如果在電腦上找到了指定的 SDK 版本，則會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-210">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="9ab95-211">如果在電腦上找不到指定的 SDK 版本，則會使用該版本的最新已安裝 SDK **修補程式版本**。</span><span class="sxs-lookup"><span data-stu-id="9ab95-211">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="9ab95-212">最新安裝的 SDK**修補程式版本**可以是發行版本或發行前版本（最高版本號碼獲勝）。</span><span class="sxs-lookup"><span data-stu-id="9ab95-212">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="9ab95-213">對於 .NET Core 2.1 和更新版本，在 SDK 選取項目中，低於指定的**修補程式版本**的**修補程式版本**會被忽略。</span><span class="sxs-lookup"><span data-stu-id="9ab95-213">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="9ab95-214">如果找不到指定的 SDK 版本和適當的 SDK **修補程式版本**，則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="9ab95-214">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="9ab95-215">SDK 版本是由下列元件所組成：</span><span class="sxs-lookup"><span data-stu-id="9ab95-215">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="9ab95-216">.NET Core SDK **功能版本**是由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的第一個數字 (`x`) 表示。</span><span class="sxs-lookup"><span data-stu-id="9ab95-216">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="9ab95-217">一般而言，.NET Core SDK 的發行週期比 .NET Core 快。</span><span class="sxs-lookup"><span data-stu-id="9ab95-217">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="9ab95-218">**修補程式版本**由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的最後兩個數字 (`yz`) 定義。</span><span class="sxs-lookup"><span data-stu-id="9ab95-218">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="9ab95-219">例如，如果指定 `2.1.300` 做為 SDK 版本，SDK 選取項目最高會找到 `2.1.399`，但是 `2.1.400` 不視為 `2.1.300` 的修補版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-219">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="9ab95-220">.NET Core SDK 版本 `2.1.100` 到 `2.1.201` 是在版本號碼轉換期間發行，它們並沒有正確地處理 `xyz` 標記法。</span><span class="sxs-lookup"><span data-stu-id="9ab95-220">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="9ab95-221">強烈建議如果您在 *global.json* 檔案中指定這些版本，則必須確保目標電腦上有這些指定的版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-221">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="9ab95-222">針對組建警告進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="9ab95-222">Troubleshoot build warnings</span></span>

* <span data-ttu-id="9ab95-223">下列警告指出您的專案是使用 .NET Core SDK 的搶鮮版來編譯：</span><span class="sxs-lookup"><span data-stu-id="9ab95-223">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="9ab95-224">您正在使用.NET Core SDK 的預覽版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-224">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="9ab95-225">您可以在目前的專案中透過 global.json 檔案定義 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-225">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="9ab95-226">詳細資訊位於 <https://go.microsoft.com/fwlink/?linkid=869452> 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-226">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="9ab95-227">.NET Core SDK 版本一向承諾提供高品質的產品。</span><span class="sxs-lookup"><span data-stu-id="9ab95-227">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="9ab95-228">不過，如果您不想要使用發行前版本，請在[allowPrerelease](#allowprerelease)區段中查看可與 .net CORE 3.0 SDK 或更新版本搭配使用的不同策略。</span><span class="sxs-lookup"><span data-stu-id="9ab95-228">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="9ab95-229">對於從未安裝 .NET Core 3.0 或更新版本的電腦，您必須*在檔案上建立global.js* ，並指定您要使用的確切版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-229">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="9ab95-230">下列警告指出您的專案目標為 EF Core 1.0 或1.1，這與 .NET Core 2.1 SDK 和更新版本不相容：</span><span class="sxs-lookup"><span data-stu-id="9ab95-230">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="9ab95-231">啟動專案 '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'。</span><span class="sxs-lookup"><span data-stu-id="9ab95-231">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="9ab95-232">這個版本的 Entity Framework Core.NET 命令列工具僅支援 2.0 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-232">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="9ab95-233">如需使用舊版工具的詳細資訊，請參閱 <https://go.microsoft.com/fwlink/?linkid=871254> 。</span><span class="sxs-lookup"><span data-stu-id="9ab95-233">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="9ab95-234">從 .NET Core 2.1 SDK (2.1.300 版) 開始，`dotnet ef` 命令會包含在 SDK 中。</span><span class="sxs-lookup"><span data-stu-id="9ab95-234">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="9ab95-235">若要編譯您的專案，請在您的電腦上安裝 .NET Core 2.0 SDK (版本 2.1.201) 或舊版，並使用*global.json* file 來定義所需的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="9ab95-235">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="9ab95-236">如需 `dotnet ef` 命令的詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="9ab95-236">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ab95-237">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ab95-237">See also</span></span>

- [<span data-ttu-id="9ab95-238">解析專案 SDK 的方式</span><span class="sxs-lookup"><span data-stu-id="9ab95-238">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
