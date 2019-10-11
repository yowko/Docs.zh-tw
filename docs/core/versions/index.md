---
title: .NET Core Runtime 與 SDK 如何進行版本設定
description: 此文章說明 .NET Core SDK 與 Runtime 如何進行版本設定 (類似語意式版本設定)。
author: bleroy
ms.date: 07/26/2018
ms.custom: seodec18
ms.openlocfilehash: b8cfb2d40b1ae88ef03daca6c31b283256bc6f26
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179963"
---
# <a name="overview-of-how-net-core-is-versioned"></a><span data-ttu-id="7e8ea-103">.NET Core 版本設定概觀</span><span class="sxs-lookup"><span data-stu-id="7e8ea-103">Overview of how .NET Core is versioned</span></span>

<span data-ttu-id="7e8ea-104">.NET Core 參考 .NET Core Runtime 與 .NET Core SDK，它包含開發應用程式所需的工具。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-104">.NET Core refers to the .NET Core Runtime and the .NET Core SDK, which contains the tools you need to develop applications.</span></span> <span data-ttu-id="7e8ea-105">.NET Core SDK 是設計來搭配任何舊版 .NET Core Runtime 使用的。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-105">.NET Core SDKs are designed to work with any previous version of the .NET Core Runtime.</span></span> <span data-ttu-id="7e8ea-106">此文章說明執行階段與 SDK 版本策略。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-106">This article explains the runtime and the SDK version strategy.</span></span> <span data-ttu-id="7e8ea-107">您可以在介紹 [.NET Standard](../../standard/net-standard.md#net-implementation-support) 的文章中找到 .NET Standard 版本號碼的解釋。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-107">An explanation of version numbers for .NET Standard can be found in the article introducing [.NET Standard](../../standard/net-standard.md#net-implementation-support).</span></span>

<span data-ttu-id="7e8ea-108">.NET Core 執行階段與 .NET Core SDK 加入不同費率的新功能：一般而言，.NET Core SDK 提供更新工具的速度比 .NET Core 執行階段變更您在生產環境中使用的執行階段的速度快。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-108">The .NET Core Runtime and .NET Core SDK add new features at a different rate - in general the .NET Core SDK provides updated tools more quickly than the .NET Core Runtime changes the runtime you use in production.</span></span>

## <a name="versioning-details"></a><span data-ttu-id="7e8ea-109">版本控制的詳細資料</span><span class="sxs-lookup"><span data-stu-id="7e8ea-109">Versioning details</span></span>

<span data-ttu-id="7e8ea-110">".NET Core 2.1" 指的是 .NET Core 執行階段版本號碼。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-110">".NET Core 2.1" refers to the .NET Core Runtime version number.</span></span> <span data-ttu-id="7e8ea-111">.NET Core 執行階段有版本控制的主要/次要/修補方法，可允許[語意式版本控制](#semantic-versioning)。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-111">The .NET Core Runtime has a major/minor/patch approach to versioning that follows [semantic versioning](#semantic-versioning).</span></span>

<span data-ttu-id="7e8ea-112">.NET Core SDK 不遵循語意式版本控制。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-112">The .NET Core SDK doesn't follow semantic versioning.</span></span> <span data-ttu-id="7e8ea-113">.NET Core SDK 發行速度比較快，而且其版本必須同時傳達對應的執行階段與 SDK 的自有次要與修補發行版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-113">The .NET Core SDK releases faster and its versions must communicate both the aligned runtime and the SDK's own minor and patch releases.</span></span> <span data-ttu-id="7e8ea-114">.NET Core SDK 版本的前兩個位置鎖定至隨著它發行的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-114">The first two positions of the .NET Core SDK version are locked to the .NET Core Runtime it released with.</span></span> <span data-ttu-id="7e8ea-115">SDK 的每個版本都可以針對此執行階段或任何較低的版本建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-115">Each version of the SDK can create applications for this runtime or any lower version.</span></span>

<span data-ttu-id="7e8ea-116">SDK 版本號碼的第三個位置同時傳達次要與修補號碼。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-116">The third position of the SDK version number communicates both the minor and patch number.</span></span> <span data-ttu-id="7e8ea-117">次要版本會被乘以 100。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-117">The minor version is multiplied by 100.</span></span> <span data-ttu-id="7e8ea-118">次要版本 1、修補版本 2 將以 102 表示。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-118">Minor version 1, patch version 2 would be represented as 102.</span></span> <span data-ttu-id="7e8ea-119">最後兩位數代表修補號碼。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-119">The final two digits represent the patch number.</span></span> <span data-ttu-id="7e8ea-120">例如，.NET Core 2.2 的發行可能會建立如下表的發行版本：</span><span class="sxs-lookup"><span data-stu-id="7e8ea-120">For example, the release of .NET Core 2.2 may create releases like the following table:</span></span>

| <span data-ttu-id="7e8ea-121">變更</span><span class="sxs-lookup"><span data-stu-id="7e8ea-121">Change</span></span>                | <span data-ttu-id="7e8ea-122">.NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="7e8ea-122">.NET Core Runtime</span></span> | <span data-ttu-id="7e8ea-123">.NET Core SDK (\*)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-123">.NET Core SDK (\*)</span></span> |
|-----------------------|-------------------|-------------------|
| <span data-ttu-id="7e8ea-124">初始版本</span><span class="sxs-lookup"><span data-stu-id="7e8ea-124">Initial release</span></span>       | <span data-ttu-id="7e8ea-125">2.2.0</span><span class="sxs-lookup"><span data-stu-id="7e8ea-125">2.2.0</span></span>             | <span data-ttu-id="7e8ea-126">2.2.100</span><span class="sxs-lookup"><span data-stu-id="7e8ea-126">2.2.100</span></span>           |
| <span data-ttu-id="7e8ea-127">SDK 修補程式</span><span class="sxs-lookup"><span data-stu-id="7e8ea-127">SDK Patch</span></span>             | <span data-ttu-id="7e8ea-128">2.2.0</span><span class="sxs-lookup"><span data-stu-id="7e8ea-128">2.2.0</span></span>             | <span data-ttu-id="7e8ea-129">2.2.101</span><span class="sxs-lookup"><span data-stu-id="7e8ea-129">2.2.101</span></span>           |
| <span data-ttu-id="7e8ea-130">執行階段與 SDK 修補程式</span><span class="sxs-lookup"><span data-stu-id="7e8ea-130">Runtime and SDK Patch</span></span> | <span data-ttu-id="7e8ea-131">2.2.1</span><span class="sxs-lookup"><span data-stu-id="7e8ea-131">2.2.1</span></span>             | <span data-ttu-id="7e8ea-132">2.2.102</span><span class="sxs-lookup"><span data-stu-id="7e8ea-132">2.2.102</span></span>           |
| <span data-ttu-id="7e8ea-133">SDK 功能變更</span><span class="sxs-lookup"><span data-stu-id="7e8ea-133">SDK Feature change</span></span>    | <span data-ttu-id="7e8ea-134">2.2.1</span><span class="sxs-lookup"><span data-stu-id="7e8ea-134">2.2.1</span></span>             | <span data-ttu-id="7e8ea-135">2.2.200</span><span class="sxs-lookup"><span data-stu-id="7e8ea-135">2.2.200</span></span>           |

<span data-ttu-id="7e8ea-136">(\*) 此圖表使用未來的 2.2 .NET Core 執行階段做為範例，因為歷史成品表示 .NET Core 2.1 的第一個 SDK 是 2.1.300。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-136">(\*) This chart uses a future 2.2 .NET Core Runtime as the example because a historic artifact meant the first SDK for .NET Core 2.1 is 2.1.300.</span></span> <span data-ttu-id="7e8ea-137">如需詳細資訊，請參閱 [.NET Core 版本選擇](selection.md)。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-137">For more information, See the [.NET Core version selection](selection.md).</span></span>

<span data-ttu-id="7e8ea-138">注意：</span><span class="sxs-lookup"><span data-stu-id="7e8ea-138">NOTES:</span></span>

- <span data-ttu-id="7e8ea-139">若 SDK 在執行階段功能更新之前有 10 個功能更新，版本號碼會滾入 1000 系列，且具有 2.2.1000 做為 2.2.900 之後的未來發行版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-139">If the SDK has 10 feature updates before a runtime feature update, version numbers roll into the 1000 series with numbers like 2.2.1000 as the feature release following 2.2.900.</span></span> <span data-ttu-id="7e8ea-140">此情況不應該發生。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-140">This situation isn't expected to occur.</span></span>
- <span data-ttu-id="7e8ea-141">不會發生沒有功能發行版本的 99 修補發行版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-141">99 patch releases without a feature release won't occur.</span></span> <span data-ttu-id="7e8ea-142">若發行版本接近此號碼，它會強制功能發行版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-142">If a release approaches this number, it forces a feature release.</span></span>

<span data-ttu-id="7e8ea-143">您可以在 [dotnet/designs](https://github.com/dotnet/designs/pull/29) 存放庫 \(英文\) 中查看此初始提案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-143">You can see more details in the initial proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="7e8ea-144">語意版本控制</span><span class="sxs-lookup"><span data-stu-id="7e8ea-144">Semantic versioning</span></span>

<span data-ttu-id="7e8ea-145">.NET Core *執行階段* 大致上遵循[語意式版本控制 (SemVer)](https://semver.org/)並採用 `MAJOR.MINOR.PATCH` 版本控制，使用版本號碼的不同部分來描述變更的程度和類型。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-145">The .NET Core *Runtime* roughly adheres to [Semantic Versioning (SemVer)](https://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="7e8ea-146">選擇性的 `PRERELEASE` 和 `BUILDNUMBER` 組件絕對不會是受支援版本的一部分，並只會存在於每日組建、來自來源目標的本機組建，以及未支援的預覽版本上。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-146">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="understand-runtime-version-number-changes"></a><span data-ttu-id="7e8ea-147">了解執行階段版本號碼變更</span><span class="sxs-lookup"><span data-stu-id="7e8ea-147">Understand runtime version number changes</span></span>

<span data-ttu-id="7e8ea-148">`MAJOR` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="7e8ea-148">`MAJOR` is incremented when:</span></span>

- <span data-ttu-id="7e8ea-149">產品或新產品方向發生重大便更。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-149">Significant changes occur to the product, or a new product direction.</span></span>
- <span data-ttu-id="7e8ea-150">接受中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-150">Breaking changes were taken.</span></span> <span data-ttu-id="7e8ea-151">接受中斷性變更的標準較高。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-151">There's a high bar to accepting breaking changes.</span></span>
- <span data-ttu-id="7e8ea-152">不再支援舊版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-152">An old version is no longer supported.</span></span>
- <span data-ttu-id="7e8ea-153">採用現有相依性的較新 `MAJOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-153">A newer `MAJOR` version of an existing dependency is adopted.</span></span>

<span data-ttu-id="7e8ea-154">`MINOR` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="7e8ea-154">`MINOR` is incremented when:</span></span>

- <span data-ttu-id="7e8ea-155">新增公用 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-155">Public API surface area is added.</span></span>
- <span data-ttu-id="7e8ea-156">新增新的行為。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-156">A new behavior is added.</span></span>
- <span data-ttu-id="7e8ea-157">採用現有相依性的較新 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-157">A newer `MINOR` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="7e8ea-158">引入新的相依性。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-158">A new dependency is introduced.</span></span>

<span data-ttu-id="7e8ea-159">`PATCH` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="7e8ea-159">`PATCH` is incremented when:</span></span>

- <span data-ttu-id="7e8ea-160">已修正 Bug。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-160">Bug fixes are made.</span></span>
- <span data-ttu-id="7e8ea-161">新增對較新平台的支援。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-161">Support for a newer platform is added.</span></span>
- <span data-ttu-id="7e8ea-162">採用現有相依性的較新 `PATCH` 版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-162">A newer `PATCH` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="7e8ea-163">任何其他不符合其中一個先前案例的變更。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-163">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="7e8ea-164">當有多項變更時，因個別變更而影響的最高項目就會遞增，而下列項目會重設為零。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-164">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="7e8ea-165">例如，當 `MAJOR` 遞增時，`MINOR` 和 `PATCH` 會重設為零。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-165">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="7e8ea-166">當 `MINOR` 遞增時，`PATCH` 會重設為零而 `MAJOR` 保持不變。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-166">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

## <a name="version-numbers-in-file-names"></a><span data-ttu-id="7e8ea-167">檔案名稱中的版本號碼</span><span class="sxs-lookup"><span data-stu-id="7e8ea-167">Version numbers in file names</span></span>

<span data-ttu-id="7e8ea-168">針對 .NET Core 下載的檔案具有版本，例如 `dotnet-sdk-2.1.300-win10-x64.exe`。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-168">The files downloaded for .NET Core carry the version, for example, `dotnet-sdk-2.1.300-win10-x64.exe`.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="7e8ea-169">預覽版本</span><span class="sxs-lookup"><span data-stu-id="7e8ea-169">Preview versions</span></span>

<span data-ttu-id="7e8ea-170">預覽版本將 `-preview[number]-([build]|"final")` 附加至版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-170">Preview versions have a `-preview[number]-([build]|"final")` appended to the version.</span></span> <span data-ttu-id="7e8ea-171">例如，`2.0.0-preview1-final`。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-171">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="7e8ea-172">服務版本</span><span class="sxs-lookup"><span data-stu-id="7e8ea-172">Servicing versions</span></span>

<span data-ttu-id="7e8ea-173">版本發行之後，版本分支通常會停止產生每日組建，改為開始產生服務組建。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-173">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="7e8ea-174">服務版本會將 `-servicing-[number]` 附加至版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-174">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="7e8ea-175">例如，`2.0.1-servicing-006924`。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-175">For example, `2.0.1-servicing-006924`.</span></span>

## <a name="relationship-to-net-standard-versions"></a><span data-ttu-id="7e8ea-176">與 .NET Standard 版本的關聯性</span><span class="sxs-lookup"><span data-stu-id="7e8ea-176">Relationship to .NET Standard versions</span></span>

<span data-ttu-id="7e8ea-177">.NET Standard 是由 .NET 參考組件所組成。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-177">.NET Standard consists of a .NET reference assembly.</span></span> <span data-ttu-id="7e8ea-178">每個平台都有多個特定實作。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-178">There are multiple implementations specific to each platform.</span></span> <span data-ttu-id="7e8ea-179">參考組件包含 .NET API 的定義，這是給定 .NET Standard 版本的一部分。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-179">The reference assembly contains the definition of .NET APIs which are part of a given .NET Standard version.</span></span> <span data-ttu-id="7e8ea-180">每個實作都履行特定平台上的 .NET Standard 合約。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-180">Each implementation fulfills the .NET Standard contract on the specific platform.</span></span> <span data-ttu-id="7e8ea-181">您可以在《.NET 指南》中的[.NET Standard](../../standard/net-standard.md) 一文深入了解 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-181">You can learn more about .NET Standard in the article on [.NET Standard](../../standard/net-standard.md) in the .NET Guide.</span></span>

<span data-ttu-id="7e8ea-182">.NET Standard 參考組件使用a `MAJOR.MINOR` 版本控制配置。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-182">The .NET Standard reference assembly uses a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="7e8ea-183">`PATCH` 對 .NET Standard 而言不實用，因為它只公開 API 規格 (無實作)，而且根據定義，對 API 所做的任何變更都會代表未來集合中的變更，亦即新的 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-183">`PATCH` level isn't useful for .NET Standard because it exposes only an API specification (no implementation) and by definition any change to the API would represent a change in the feature set, and thus a new `MINOR` version.</span></span>

<span data-ttu-id="7e8ea-184">可能可以更新每個平台上的實作，通常是做為平台發行版本的一部分，因此對在該平台上使用 .NET Standard 的開發人員而言並非顯而易見。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-184">The implementations on each platform may be updated, typically as part of the platform release, and thus not evident to the programmers using .NET Standard on that platform.</span></span>

<span data-ttu-id="7e8ea-185">.NET Core 的每個版本都實作 .NET Standard. 的版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-185">Each version of .NET Core implements a version of .NET Standard.</span></span> <span data-ttu-id="7e8ea-186">實作 .NET Standard 的版本意指支援舊版 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-186">Implementing a version of .NET Standard implies support for previous versions of .NET Standard.</span></span> <span data-ttu-id="7e8ea-187">.NET Standard 與 .NET Core 版本彼此獨立。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-187">.NET Standard and .NET Core version independently.</span></span> <span data-ttu-id="7e8ea-188">.NET Core 2.0 實作 .NET Standard 2.0 只是巧合。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-188">It's a coincidence that .NET Core 2.0 implements .NET Standard 2.0.</span></span> <span data-ttu-id="7e8ea-189">.NET Core 2.1 也實作 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-189">.NET Core 2.1 also implements .NET Standard 2.0.</span></span> <span data-ttu-id="7e8ea-190">.NET Core 將支援未來推出的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="7e8ea-190">.NET Core will support future versions of .NET Standard as they become available.</span></span>

| <span data-ttu-id="7e8ea-191">.NET Core</span><span class="sxs-lookup"><span data-stu-id="7e8ea-191">.NET Core</span></span> | <span data-ttu-id="7e8ea-192">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7e8ea-192">.NET Standard</span></span> |
|-----------|---------------|
| <span data-ttu-id="7e8ea-193">1.0</span><span class="sxs-lookup"><span data-stu-id="7e8ea-193">1.0</span></span>       | <span data-ttu-id="7e8ea-194">最高到 1.6</span><span class="sxs-lookup"><span data-stu-id="7e8ea-194">up to 1.6</span></span>     |
| <span data-ttu-id="7e8ea-195">2.0</span><span class="sxs-lookup"><span data-stu-id="7e8ea-195">2.0</span></span>       | <span data-ttu-id="7e8ea-196">最高到 2.0</span><span class="sxs-lookup"><span data-stu-id="7e8ea-196">up to 2.0</span></span>     |
| <span data-ttu-id="7e8ea-197">2.1</span><span class="sxs-lookup"><span data-stu-id="7e8ea-197">2.1</span></span>       | <span data-ttu-id="7e8ea-198">最高到 2.0</span><span class="sxs-lookup"><span data-stu-id="7e8ea-198">up to 2.0</span></span>     |
| <span data-ttu-id="7e8ea-199">2.2</span><span class="sxs-lookup"><span data-stu-id="7e8ea-199">2.2</span></span>       | <span data-ttu-id="7e8ea-200">最高到 2.0</span><span class="sxs-lookup"><span data-stu-id="7e8ea-200">up to 2.0</span></span>     |
| <span data-ttu-id="7e8ea-201">3.0</span><span class="sxs-lookup"><span data-stu-id="7e8ea-201">3.0</span></span>       | <span data-ttu-id="7e8ea-202">最多2。1</span><span class="sxs-lookup"><span data-stu-id="7e8ea-202">up to 2.1</span></span>     |

## <a name="see-also"></a><span data-ttu-id="7e8ea-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e8ea-203">See also</span></span>

- [<span data-ttu-id="7e8ea-204">目標架構</span><span class="sxs-lookup"><span data-stu-id="7e8ea-204">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="7e8ea-205">.NET Core 發佈封裝</span><span class="sxs-lookup"><span data-stu-id="7e8ea-205">.NET Core distribution packaging</span></span>](../build/distribution-packaging.md)
- [<span data-ttu-id="7e8ea-206">.NET Core 支援週期資料表</span><span class="sxs-lookup"><span data-stu-id="7e8ea-206">.NET Core Support Lifecycle Fact Sheet</span></span>](https://dotnet.microsoft.com/platform/support/policy)
- <span data-ttu-id="7e8ea-207">[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3) (.NET Core 2+ 版本繫結)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-207">[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3)</span></span>
- <span data-ttu-id="7e8ea-208">[.NET Core 的 Docker 映像](https://hub.docker.com/_/microsoft-dotnet-core/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="7e8ea-208">[Docker images for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)</span></span>
