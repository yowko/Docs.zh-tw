---
title: global.json 概觀
description: 了解如何使用 global.json 檔案來設定執行.NET Core CLI 命令時的 NET Core SDK 版本。
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 714e32ec841cee214f801de65bccf0041af66b0b
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281541"
---
# <a name="globaljson-overview"></a><span data-ttu-id="1ade0-103">global.json 概觀</span><span class="sxs-lookup"><span data-stu-id="1ade0-103">global.json overview</span></span>

<span data-ttu-id="1ade0-104">本文 **適用于：** ✔️ .net CORE 2.0 SDK 和更新版本</span><span class="sxs-lookup"><span data-stu-id="1ade0-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="1ade0-105">*global.json* 檔案可讓您定義執行.NET Core CLI 命令時所使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="1ade0-106">選取 .NET Core SDK 與指定專案所針對的執行階段沒有關係。</span><span class="sxs-lookup"><span data-stu-id="1ade0-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="1ade0-107">.NET Core SDK 版本會指出所使用的 .NET Core CLI 版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="1ade0-108">一般而言，您會想要使用最新版的 SDK 工具，因此不需要 *global.js* 檔案。</span><span class="sxs-lookup"><span data-stu-id="1ade0-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="1ade0-109">在某些 advanced 案例中，您可能會想要控制 SDK 工具的版本，而本文將說明如何進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="1ade0-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="1ade0-110">如需改為指定執行階段的詳細資訊，請參閱[目標架構](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="1ade0-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="1ade0-111">.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找 *global.json* 檔案。</span><span class="sxs-lookup"><span data-stu-id="1ade0-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="1ade0-112">global.json 結構描述</span><span class="sxs-lookup"><span data-stu-id="1ade0-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="1ade0-113">sdk</span><span class="sxs-lookup"><span data-stu-id="1ade0-113">sdk</span></span>

<span data-ttu-id="1ade0-114">輸入： `object`</span><span class="sxs-lookup"><span data-stu-id="1ade0-114">Type: `object`</span></span>

<span data-ttu-id="1ade0-115">指定要選取 .NET Core SDK 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1ade0-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="1ade0-116">version</span><span class="sxs-lookup"><span data-stu-id="1ade0-116">version</span></span>

- <span data-ttu-id="1ade0-117">輸入： `string`</span><span class="sxs-lookup"><span data-stu-id="1ade0-117">Type: `string`</span></span>

- <span data-ttu-id="1ade0-118">提供自： .NET Core 1.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="1ade0-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="1ade0-119">要使用的 .NET Core SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="1ade0-120">此欄位：</span><span class="sxs-lookup"><span data-stu-id="1ade0-120">This field:</span></span>

- <span data-ttu-id="1ade0-121">沒有萬用字元支援，也就是必須指定完整的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1ade0-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="1ade0-122">不支援版本範圍。</span><span class="sxs-lookup"><span data-stu-id="1ade0-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="1ade0-123">allowPrerelease</span><span class="sxs-lookup"><span data-stu-id="1ade0-123">allowPrerelease</span></span>

- <span data-ttu-id="1ade0-124">輸入： `boolean`</span><span class="sxs-lookup"><span data-stu-id="1ade0-124">Type: `boolean`</span></span>

- <span data-ttu-id="1ade0-125">提供自： .NET Core 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="1ade0-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="1ade0-126">指出當您選取要使用的 SDK 版本時，SDK 解析程式是否應考慮發行前版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="1ade0-127">如果您未明確設定此值，預設值將取決於您是否從 Visual Studio 執行：</span><span class="sxs-lookup"><span data-stu-id="1ade0-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="1ade0-128">如果您 **不** 是 Visual Studio，預設值為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="1ade0-129">如果您在 Visual Studio 中，它會使用所要求的發行前版本狀態。</span><span class="sxs-lookup"><span data-stu-id="1ade0-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="1ade0-130">亦即，如果您使用預覽版本的 Visual Studio，或在 [ **工具** 選項環境預覽) 功能] 下設定 .NET Core SDK (選項的 [ **使用預覽** ]  >  **Options**  >  **Environment**  >  **Preview Features** ，則預設值為 `true` ; 否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features** ), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="1ade0-131">向前復原</span><span class="sxs-lookup"><span data-stu-id="1ade0-131">rollForward</span></span>

- <span data-ttu-id="1ade0-132">輸入： `string`</span><span class="sxs-lookup"><span data-stu-id="1ade0-132">Type: `string`</span></span>

- <span data-ttu-id="1ade0-133">提供自： .NET Core 3.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="1ade0-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="1ade0-134">選取 SDK 版本時所要使用的向前復原原則，可在特定 SDK 版本遺失或作為指示詞使用較高版本時作為復原。</span><span class="sxs-lookup"><span data-stu-id="1ade0-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="1ade0-135">必須以值指定 [版本](#version) `rollForward` ，除非您將它設定為 `latestMajor` 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>
<span data-ttu-id="1ade0-136">預設向前復原行為取決於 [相符的規則](#matching-rules)。</span><span class="sxs-lookup"><span data-stu-id="1ade0-136">The default roll forward behavior is determined by the [matching rules](#matching-rules).</span></span>

<span data-ttu-id="1ade0-137">若要瞭解可用的原則及其行為，請考慮下列格式的 SDK 版本定義 `x.y.znn` ：</span><span class="sxs-lookup"><span data-stu-id="1ade0-137">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="1ade0-138">`x` 這是主要版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-138">`x` is the major version.</span></span>
- <span data-ttu-id="1ade0-139">`y` 這是次要版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-139">`y` is the minor version.</span></span>
- <span data-ttu-id="1ade0-140">`z` 是功能區。</span><span class="sxs-lookup"><span data-stu-id="1ade0-140">`z` is the feature band.</span></span>
- <span data-ttu-id="1ade0-141">`nn` 這是修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-141">`nn` is the patch version.</span></span>

<span data-ttu-id="1ade0-142">下表顯示索引鍵的可能值 `rollForward` ：</span><span class="sxs-lookup"><span data-stu-id="1ade0-142">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="1ade0-143">值</span><span class="sxs-lookup"><span data-stu-id="1ade0-143">Value</span></span>         | <span data-ttu-id="1ade0-144">行為</span><span class="sxs-lookup"><span data-stu-id="1ade0-144">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="1ade0-145">使用指定的版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-145">Uses the specified version.</span></span> <br> <span data-ttu-id="1ade0-146">如果找不到，會向前復原到最新的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-146">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="1ade0-147">如果找不到，會失敗。</span><span class="sxs-lookup"><span data-stu-id="1ade0-147">If not found, fails.</span></span> <br><br> <span data-ttu-id="1ade0-148">此值是舊版 SDK 的舊版行為。</span><span class="sxs-lookup"><span data-stu-id="1ade0-148">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="1ade0-149">針對指定的主要、次要和功能區，使用最新的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-149">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="1ade0-150">如果找不到，會向前復原到相同主要/次要內的下一個較高的功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-150">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="1ade0-151">如果找不到，會失敗。</span><span class="sxs-lookup"><span data-stu-id="1ade0-151">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="1ade0-152">針對指定的主要、次要和功能區，使用最新的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-152">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="1ade0-153">如果找不到，會向前復原到相同主要/次要版本內的下一個較高的功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-153">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="1ade0-154">如果找不到，會向前復原到相同主要位置內的下一個較高次要和功能頻外，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-154">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="1ade0-155">如果找不到，會失敗。</span><span class="sxs-lookup"><span data-stu-id="1ade0-155">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="1ade0-156">針對指定的主要、次要和功能區，使用最新的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-156">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="1ade0-157">如果找不到，會向前復原到相同主要/次要版本內的下一個較高的功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-157">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="1ade0-158">如果找不到，會向前復原到相同主要位置內的下一個較高次要和功能頻外，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-158">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="1ade0-159">如果找不到，會向前復原到下一個較高的主要、次要和功能區，並使用該功能區的最新修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-159">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="1ade0-160">如果找不到，會失敗。</span><span class="sxs-lookup"><span data-stu-id="1ade0-160">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="1ade0-161">使用最新安裝的修補程式等級，此層級符合要求的主要、次要和功能頻的修補程式等級，且大於或等於指定的值。</span><span class="sxs-lookup"><span data-stu-id="1ade0-161">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="1ade0-162">如果找不到，會失敗。</span><span class="sxs-lookup"><span data-stu-id="1ade0-162">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="1ade0-163">使用最高安裝的功能區和修補程式等級，其符合要求的主要和次要，以及大於或等於指定值的功能區和修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-163">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="1ade0-164">如果找不到，會失敗。</span><span class="sxs-lookup"><span data-stu-id="1ade0-164">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="1ade0-165">使用最高安裝的次要、功能區和修補程式層級，以符合所要求的主要次要、功能區，以及大於或等於指定值的修補程式等級。</span><span class="sxs-lookup"><span data-stu-id="1ade0-165">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor, feature band, and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="1ade0-166">如果找不到，會失敗。</span><span class="sxs-lookup"><span data-stu-id="1ade0-166">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="1ade0-167">使用已安裝的最高 .NET Core SDK，其版本大於或等於指定的值。</span><span class="sxs-lookup"><span data-stu-id="1ade0-167">Uses the highest installed .NET Core SDK with a version that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="1ade0-168">如果找不到，會失敗。</span><span class="sxs-lookup"><span data-stu-id="1ade0-168">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="1ade0-169">不向前復原。</span><span class="sxs-lookup"><span data-stu-id="1ade0-169">Doesn't roll forward.</span></span> <span data-ttu-id="1ade0-170">需要完全相符。</span><span class="sxs-lookup"><span data-stu-id="1ade0-170">Exact match required.</span></span> |

### <a name="msbuild-sdks"></a><span data-ttu-id="1ade0-171">msbuild-sdk</span><span class="sxs-lookup"><span data-stu-id="1ade0-171">msbuild-sdks</span></span>

<span data-ttu-id="1ade0-172">輸入： `object`</span><span class="sxs-lookup"><span data-stu-id="1ade0-172">Type: `object`</span></span>

<span data-ttu-id="1ade0-173">可讓您在單一位置（而不是每個個別專案）控制專案 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-173">Lets you control the project SDK version in one place rather than in each individual project.</span></span> <span data-ttu-id="1ade0-174">如需詳細資訊，請參閱 [如何解析專案 sdk](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)。</span><span class="sxs-lookup"><span data-stu-id="1ade0-174">For more information, see [How project SDKs are resolved](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span></span>

## <a name="examples"></a><span data-ttu-id="1ade0-175">範例</span><span class="sxs-lookup"><span data-stu-id="1ade0-175">Examples</span></span>

<span data-ttu-id="1ade0-176">下列範例顯示如何使用發行前版本：</span><span class="sxs-lookup"><span data-stu-id="1ade0-176">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="1ade0-177">下列範例會示範如何使用安裝的最高版本，且該版本大於或等於指定的版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-177">The following example shows how to use the highest version installed that is greater or equal than the specified version.</span></span> <span data-ttu-id="1ade0-178">所顯示的 JSON 不允許任何早于2.2.200 的 SDK 版本，並且允許2.2.200 或任何較新的版本，包括3.0.xxx 和3.1.xxx。</span><span class="sxs-lookup"><span data-stu-id="1ade0-178">The JSON shown disallows any SDK version earlier than 2.2.200 and allows 2.2.200 or any later version, including 3.0.xxx and 3.1.xxx.</span></span>

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="1ade0-179">下列範例顯示如何使用確切指定的版本：</span><span class="sxs-lookup"><span data-stu-id="1ade0-179">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="1ade0-180">下列範例顯示如何使用安裝在特定主要和次要版本的最新功能區和修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-180">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version.</span></span> <span data-ttu-id="1ade0-181">所顯示的 JSON 不允許任何早于3.1.102 的 SDK 版本，並且允許3.1.102 或任何較新的3.1.xxx 版本，例如3.1.103 或3.1.200。</span><span class="sxs-lookup"><span data-stu-id="1ade0-181">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.xxx version, such as 3.1.103 or 3.1.200.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="1ade0-182">下列範例顯示如何使用安裝在特定版本的最高修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-182">The following example shows how to use the highest patch version installed of a specific version.</span></span> <span data-ttu-id="1ade0-183">所顯示的 JSON 不允許任何早于3.1.102 的 SDK 版本，並且允許3.1.102 或任何較新的 3.1.1 xx 版本（例如3.1.103 或3.1.199）。</span><span class="sxs-lookup"><span data-stu-id="1ade0-183">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.1xx version, such as 3.1.103 or 3.1.199.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="1ade0-184">global.json 和.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="1ade0-184">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="1ade0-185">瞭解您電腦上安裝的 SDK 版本，以在 *global.js* 檔案中設定一個 SDK 會很有説明。</span><span class="sxs-lookup"><span data-stu-id="1ade0-185">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="1ade0-186">如需如何進行這項操作的詳細資訊，請參閱 [如何檢查是否已安裝 .Net Core](../install/how-to-detect-installed-versions.md#check-sdk-versions)。</span><span class="sxs-lookup"><span data-stu-id="1ade0-186">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="1ade0-187">若要在您的電腦上安裝其他 .NET Core SDK 版本，請造訪 [下載 .Net Core](https://dotnet.microsoft.com/download/dotnet-core) 頁面。</span><span class="sxs-lookup"><span data-stu-id="1ade0-187">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="1ade0-188">執行 [dotnet new](dotnet-new.md) 命令，可在目前的目錄中建立新的 *global.json* 檔案，與下面的範例類似：</span><span class="sxs-lookup"><span data-stu-id="1ade0-188">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="1ade0-189">比對規則</span><span class="sxs-lookup"><span data-stu-id="1ade0-189">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="1ade0-190">比對規則是由 `dotnet.exe` 進入點所控制，這在所有已安裝的 .Net Core 安裝的執行時間中都很常見。</span><span class="sxs-lookup"><span data-stu-id="1ade0-190">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="1ade0-191">當您並存安裝多個執行時間，或者或您使用的是檔案 *上的global.js* 時，會使用最新安裝的 .Net Core 執行時間版本的比對規則。</span><span class="sxs-lookup"><span data-stu-id="1ade0-191">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side or if or you're using a *global.json* file.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="1ade0-192">.NET Core 3.x</span><span class="sxs-lookup"><span data-stu-id="1ade0-192">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="1ade0-193">從 .NET Core 3.0 開始，判斷要使用的 SDK 版本時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="1ade0-193">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="1ade0-194">如果找不到檔案 *上的global.js* ，或 *global.js* 未指定 SDK 版本或 `allowPrerelease` 值，則會使用最高安裝的 sdk 版本 (等同于設定 `rollForward` 為 `latestMajor`) 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-194">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="1ade0-195">是否考慮預先發行版本 SDK 版本取決於叫用的方式 `dotnet` 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-195">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="1ade0-196">如果您 **不** 是 Visual Studio，則會考慮發行前版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-196">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="1ade0-197">如果您在 Visual Studio 中，它會使用所要求的發行前版本狀態。</span><span class="sxs-lookup"><span data-stu-id="1ade0-197">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="1ade0-198">亦即，如果您使用預覽版本的 Visual Studio，或在 [ **工具** 選項環境預覽) 功能] 下設定 .NET Core SDK (選項的 [ **使用預覽** ]  >  **Options**  >  **Environment**  >  **Preview Features** ，則會考慮發行前版本，否則只會考慮發行版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-198">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features** ), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="1ade0-199">如果找到的 *global.js* 檔案未指定 SDK 版本，但卻指定了 `allowPrerelease` 值，則會使用最高安裝的 SDK 版本， (等同于設定 `rollForward` 為 `latestMajor`) 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-199">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="1ade0-200">最新的 SDK 版本是否可以是發行版本或發行前版本，視的值而定 `allowPrerelease` 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-200">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="1ade0-201">`true` 表示已考慮發行前版本; `false` 指出只考慮發行版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-201">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="1ade0-202">如果找到檔案 *上的global.js* ，並指定 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="1ade0-202">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="1ade0-203">如果未 `rollForward` 設定任何值，則會使用 `latestPatch` 做為預設 `rollForward` 原則。</span><span class="sxs-lookup"><span data-stu-id="1ade0-203">If no `rollForward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="1ade0-204">否則，請檢查 [向前復原](#rollforward) 區段中的每個值和其行為。</span><span class="sxs-lookup"><span data-stu-id="1ade0-204">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="1ade0-205">AllowPrerelease 一節會說明是否考慮發行前版本，以及 `allowPrerelease` 未設定的預設行為。 [allowPrerelease](#allowprerelease)</span><span class="sxs-lookup"><span data-stu-id="1ade0-205">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="1ade0-206">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1ade0-206">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="1ade0-207">在 .NET Core 2.x SDK 中，判斷要使用的 SDK 版本時，適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="1ade0-207">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="1ade0-208">如果找不到 *global.json* 檔案或 *global.json* 沒有指定 SDK 版本，則會使用最新安裝的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-208">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="1ade0-209">最新的 SDK 版本可以是發行版本或發行前版本-最高的版本號碼獲勝。</span><span class="sxs-lookup"><span data-stu-id="1ade0-209">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="1ade0-210">如果 *global.json* 未指定 SDK 版本：</span><span class="sxs-lookup"><span data-stu-id="1ade0-210">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="1ade0-211">如果在電腦上找到了指定的 SDK 版本，則會使用這個版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-211">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="1ade0-212">如果在電腦上找不到指定的 SDK 版本，則會使用該版本的最新已安裝 SDK **修補程式版本** 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-212">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="1ade0-213">最新安裝的 SDK **修補程式版本** 可以是發行版本或發行前版本-最高的版本號碼獲勝。</span><span class="sxs-lookup"><span data-stu-id="1ade0-213">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="1ade0-214">對於 .NET Core 2.1 和更新版本，在 SDK 選取項目中，低於指定的 **修補程式版本** 的 **修補程式版本** 會被忽略。</span><span class="sxs-lookup"><span data-stu-id="1ade0-214">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="1ade0-215">如果找不到指定的 SDK 版本和適當的 SDK **修補程式版本** ，則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="1ade0-215">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="1ade0-216">SDK 版本是由下列元件所組成：</span><span class="sxs-lookup"><span data-stu-id="1ade0-216">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="1ade0-217">.NET Core SDK **功能版本** 是由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的第一個數字 (`x`) 表示。</span><span class="sxs-lookup"><span data-stu-id="1ade0-217">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="1ade0-218">一般而言，.NET Core SDK 的發行週期比 .NET Core 快。</span><span class="sxs-lookup"><span data-stu-id="1ade0-218">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="1ade0-219">**修補程式版本** 由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的最後兩個數字 (`yz`) 定義。</span><span class="sxs-lookup"><span data-stu-id="1ade0-219">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="1ade0-220">例如，如果指定 `2.1.300` 做為 SDK 版本，SDK 選取項目最高會找到 `2.1.399`，但是 `2.1.400` 不視為 `2.1.300` 的修補版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-220">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="1ade0-221">.NET Core SDK 版本 `2.1.100` 到 `2.1.201` 是在版本號碼轉換期間發行，它們並沒有正確地處理 `xyz` 標記法。</span><span class="sxs-lookup"><span data-stu-id="1ade0-221">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="1ade0-222">強烈建議如果您在 *global.json* 檔案中指定這些版本，則必須確保目標電腦上有這些指定的版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-222">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="1ade0-223">針對組建警告進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1ade0-223">Troubleshoot build warnings</span></span>

* <span data-ttu-id="1ade0-224">下列警告指出您的專案是使用發行前版本的 .NET Core SDK 進行編譯：</span><span class="sxs-lookup"><span data-stu-id="1ade0-224">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="1ade0-225">您正在使用.NET Core SDK 的預覽版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-225">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="1ade0-226">您可以在目前的專案中透過 global.json 檔案定義 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-226">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="1ade0-227">詳細資訊請參閱 <https://go.microsoft.com/fwlink/?linkid=869452> 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-227">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="1ade0-228">.NET Core SDK 版本一向承諾提供高品質的產品。</span><span class="sxs-lookup"><span data-stu-id="1ade0-228">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="1ade0-229">但是，如果您不想要使用發行前版本，請在 [allowPrerelease](#allowprerelease) 區段中，檢查您可以與 .net CORE 3.0 SDK 或更新版本搭配使用的不同策略。</span><span class="sxs-lookup"><span data-stu-id="1ade0-229">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="1ade0-230">針對尚未安裝 .NET Core 3.0 或更高版本執行時間或 SDK 的電腦，您必須 *在檔案上建立global.js* ，並指定您想要使用的確切版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-230">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="1ade0-231">下列警告指出您的專案目標 EF Core 1.0 或1.1，與 .NET Core 2.1 SDK 和更新版本不相容：</span><span class="sxs-lookup"><span data-stu-id="1ade0-231">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="1ade0-232">啟動專案 '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'。</span><span class="sxs-lookup"><span data-stu-id="1ade0-232">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="1ade0-233">這個版本的 Entity Framework Core.NET 命令列工具僅支援 2.0 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-233">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="1ade0-234">如需使用舊版工具的詳細資訊，請參閱 <https://go.microsoft.com/fwlink/?linkid=871254> 。</span><span class="sxs-lookup"><span data-stu-id="1ade0-234">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="1ade0-235">從 .NET Core 2.1 SDK (2.1.300 版) 開始，`dotnet ef` 命令會包含在 SDK 中。</span><span class="sxs-lookup"><span data-stu-id="1ade0-235">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="1ade0-236">若要編譯您的專案，請在您的電腦上安裝 .NET Core 2.0 SDK (版本 2.1.201) 或更早版本，並使用 *global.json* file 定義所需的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="1ade0-236">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="1ade0-237">如需 `dotnet ef` 命令的詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。</span><span class="sxs-lookup"><span data-stu-id="1ade0-237">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ade0-238">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ade0-238">See also</span></span>

- [<span data-ttu-id="1ade0-239">解析專案 SDK 的方式</span><span class="sxs-lookup"><span data-stu-id="1ade0-239">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
