---
title: .NET Core 版本控制
description: 了解 .NET Core 的版本控制運作方式。
author: bleroy
ms.author: mairaw
ms.date: 07/26/2018
ms.openlocfilehash: 9f77709abf59d5346bf5e3c6f512cfabbf9e50de
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188465"
---
# <a name="net-core-versioning"></a><span data-ttu-id="e2c04-103">.NET Core 版本控制</span><span class="sxs-lookup"><span data-stu-id="e2c04-103">.NET Core versioning</span></span>

<span data-ttu-id="e2c04-104">.NET Core 參考 .NET Core Runtime 與 .NET Core SDK，它包含開發應用程式所需的工具。</span><span class="sxs-lookup"><span data-stu-id="e2c04-104">.NET Core refers to the .NET Core Runtime and the .NET Core SDK, which contains the tools you need to develop applications.</span></span> <span data-ttu-id="e2c04-105">.NET Core SDK 是設計來搭配任何舊版 .NET Core Runtime 使用的。</span><span class="sxs-lookup"><span data-stu-id="e2c04-105">.NET Core SDKs are designed to work with any previous version of the .NET Core Runtime.</span></span> <span data-ttu-id="e2c04-106">此文章說明執行階段與 SDK 版本策略。</span><span class="sxs-lookup"><span data-stu-id="e2c04-106">This article explains the runtime and the SDK version strategy.</span></span> <span data-ttu-id="e2c04-107">您可以在介紹 [.NET Standard](../../standard/net-standard.md#net-implementation-support) 的文章中找到 .NET Standard 版本號碼的解釋。</span><span class="sxs-lookup"><span data-stu-id="e2c04-107">An explanation of version numbers for .NET Standard can be found in the article introducing [.NET Standard](../../standard/net-standard.md#net-implementation-support).</span></span>

<span data-ttu-id="e2c04-108">.NET Core 執行階段與 .NET Core SDK 加入不同費率的新功能：一般而言，.NET Core SDK 提供更新工具的速度比 .NET Core 執行階段變更您在生產環境中使用的執行階段的速度快。</span><span class="sxs-lookup"><span data-stu-id="e2c04-108">The .NET Core Runtime and .NET Core SDK add new features at a different rate - in general the .NET Core SDK provides updated tools more quickly than the .NET Core Runtime changes the runtime you use in production.</span></span> <span data-ttu-id="e2c04-109">不幸的是，此問題在過去幾年已造成數個版本控制策略。</span><span class="sxs-lookup"><span data-stu-id="e2c04-109">Unfortunately, this problem has resulted in several versioning strategies over the last few years.</span></span> <span data-ttu-id="e2c04-110">您可以在 [.NET Core 版本控制](version-history.md)一文中了解歷史記錄。</span><span class="sxs-lookup"><span data-stu-id="e2c04-110">You can learn about the history in the article on [.NET Core versioning](version-history.md).</span></span>

## <a name="versioning-details"></a><span data-ttu-id="e2c04-111">版本控制的詳細資料</span><span class="sxs-lookup"><span data-stu-id="e2c04-111">Versioning details</span></span>

<span data-ttu-id="e2c04-112">".NET Core 2.1" 指的是 .NET Core 執行階段版本號碼。</span><span class="sxs-lookup"><span data-stu-id="e2c04-112">".NET Core 2.1" refers to the .NET Core Runtime version number.</span></span> <span data-ttu-id="e2c04-113">.NET Core 執行階段有版本控制的主要/次要/修補方法，可允許[語意式版本控制](#semantic-versioning)。</span><span class="sxs-lookup"><span data-stu-id="e2c04-113">The .NET Core Runtime has a major/minor/patch approach to versioning that follows [semantic versioning](#semantic-versioning).</span></span>

<span data-ttu-id="e2c04-114">.NET Core SDK 不遵循語意式版本控制。</span><span class="sxs-lookup"><span data-stu-id="e2c04-114">The .NET Core SDK doesn't follow semantic versioning.</span></span> <span data-ttu-id="e2c04-115">.NET Core SDK 發行速度比較快，而且其版本必須同時傳達對應的執行階段與 SDK 的自有次要與修補發行版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-115">The .NET Core SDK releases faster and its versions must communicate both the aligned runtime and the SDK's own minor and patch releases.</span></span> <span data-ttu-id="e2c04-116">.NET Core SDK 版本的前兩個位置鎖定至隨著它發行的 .NET Core 執行階段。</span><span class="sxs-lookup"><span data-stu-id="e2c04-116">The first two positions of the .NET Core SDK version are locked to the .NET Core Runtime it released with.</span></span> <span data-ttu-id="e2c04-117">SDK 的每個版本都可以針對此執行階段或任何較低的版本建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="e2c04-117">Each version of the SDK can create applications for this runtime or any lower version.</span></span>

<span data-ttu-id="e2c04-118">SDK 版本號碼的第三個位置同時傳達次要與修補號碼。</span><span class="sxs-lookup"><span data-stu-id="e2c04-118">The third position of the SDK version number communicates both the minor and patch number.</span></span> <span data-ttu-id="e2c04-119">次要版本會被乘以 100。</span><span class="sxs-lookup"><span data-stu-id="e2c04-119">The minor version is multiplied by 100.</span></span> <span data-ttu-id="e2c04-120">次要版本 1、修補版本 2 將以 102 表示。</span><span class="sxs-lookup"><span data-stu-id="e2c04-120">Minor version 1, patch version 2 would be represented as 102.</span></span> <span data-ttu-id="e2c04-121">最後兩位數代表修補號碼。</span><span class="sxs-lookup"><span data-stu-id="e2c04-121">The final two digits represent the patch number.</span></span> <span data-ttu-id="e2c04-122">例如，.NET Core 2.2 的發行可能會建立如下表的發行版本：</span><span class="sxs-lookup"><span data-stu-id="e2c04-122">For example, the release of .NET Core 2.2 may create releases like the following table:</span></span>

| <span data-ttu-id="e2c04-123">變更</span><span class="sxs-lookup"><span data-stu-id="e2c04-123">Change</span></span>                | <span data-ttu-id="e2c04-124">.NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="e2c04-124">.NET Core Runtime</span></span> | <span data-ttu-id="e2c04-125">.NET Core SDK (\*)</span><span class="sxs-lookup"><span data-stu-id="e2c04-125">.NET Core SDK (\*)</span></span> |
|-----------------------|-------------------|-------------------|
| <span data-ttu-id="e2c04-126">初始版本</span><span class="sxs-lookup"><span data-stu-id="e2c04-126">Initial release</span></span>       | <span data-ttu-id="e2c04-127">2.2.0</span><span class="sxs-lookup"><span data-stu-id="e2c04-127">2.2.0</span></span>             | <span data-ttu-id="e2c04-128">2.2.100</span><span class="sxs-lookup"><span data-stu-id="e2c04-128">2.2.100</span></span>           |
| <span data-ttu-id="e2c04-129">SDK 修補程式</span><span class="sxs-lookup"><span data-stu-id="e2c04-129">SDK Patch</span></span>             | <span data-ttu-id="e2c04-130">2.2.0</span><span class="sxs-lookup"><span data-stu-id="e2c04-130">2.2.0</span></span>             | <span data-ttu-id="e2c04-131">2.2.101</span><span class="sxs-lookup"><span data-stu-id="e2c04-131">2.2.101</span></span>           |
| <span data-ttu-id="e2c04-132">執行階段與 SDK 修補程式</span><span class="sxs-lookup"><span data-stu-id="e2c04-132">Runtime and SDK Patch</span></span> | <span data-ttu-id="e2c04-133">2.2.1</span><span class="sxs-lookup"><span data-stu-id="e2c04-133">2.2.1</span></span>             | <span data-ttu-id="e2c04-134">2.2.102</span><span class="sxs-lookup"><span data-stu-id="e2c04-134">2.2.102</span></span>           |
| <span data-ttu-id="e2c04-135">SDK 功能變更</span><span class="sxs-lookup"><span data-stu-id="e2c04-135">SDK Feature change</span></span>    | <span data-ttu-id="e2c04-136">2.2.1</span><span class="sxs-lookup"><span data-stu-id="e2c04-136">2.2.1</span></span>             | <span data-ttu-id="e2c04-137">2.2.200</span><span class="sxs-lookup"><span data-stu-id="e2c04-137">2.2.200</span></span>           |

<span data-ttu-id="e2c04-138">(\*) 此圖表使用未來的 2.2 .NET Core 執行階段做為範例，因為歷史成品表示 .NET Core 2.1 的第一個 SDK 是 2.1.300。</span><span class="sxs-lookup"><span data-stu-id="e2c04-138">(\*) This chart uses a future 2.2 .NET Core Runtime as the example because a historic artifact meant the first SDK for .NET Core 2.1 is 2.1.300.</span></span> <span data-ttu-id="e2c04-139">如需詳細資訊，請參閱 [.NET Core 版本控制的歷史](version-history.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c04-139">For more information, See the [history of .NET Core versioning](version-history.md).</span></span>

<span data-ttu-id="e2c04-140">注意：</span><span class="sxs-lookup"><span data-stu-id="e2c04-140">NOTES:</span></span>

* <span data-ttu-id="e2c04-141">若 SDK 在執行階段功能更新之前有 10 個功能更新，版本號碼會滾入 1000 系列，且具有 2.2.1000 做為 2.2.900 之後的未來發行版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-141">If the SDK has 10 feature updates before a runtime feature update, version numbers roll into the 1000 series with numbers like 2.2.1000 as the feature release following 2.2.900.</span></span> <span data-ttu-id="e2c04-142">此情況不應該發生。</span><span class="sxs-lookup"><span data-stu-id="e2c04-142">This situation isn't expected to occur.</span></span>
* <span data-ttu-id="e2c04-143">不會發生沒有功能發行版本的 99 修補發行版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-143">99 patch releases without a feature release won't occur.</span></span> <span data-ttu-id="e2c04-144">若發行版本接近此號碼，它會強制功能發行版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-144">If a release approaches this number, it forces a feature release.</span></span>

<span data-ttu-id="e2c04-145">您可以在 [dotnet/designs](https://github.com/dotnet/designs/pull/29) 存放庫 \(英文\) 中查看此初始提案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e2c04-145">You can see more details in the initial proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="e2c04-146">語意版本控制</span><span class="sxs-lookup"><span data-stu-id="e2c04-146">Semantic versioning</span></span>

<span data-ttu-id="e2c04-147">.NET Core *執行階段* 大致上遵循[語意式版本控制 (SemVer)](https://semver.org/)並採用 `MAJOR.MINOR.PATCH` 版本控制，使用版本號碼的不同部分來描述變更的程度和類型。</span><span class="sxs-lookup"><span data-stu-id="e2c04-147">The .NET Core *Runtime* roughly adheres to [Semantic Versioning (SemVer)](https://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="e2c04-148">選擇性的 `PRERELEASE` 和 `BUILDNUMBER` 組件絕對不會是受支援版本的一部分，並只會存在於每日組建、來自來源目標的本機組建，以及未支援的預覽版本上。</span><span class="sxs-lookup"><span data-stu-id="e2c04-148">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="understand-runtime-version-number-changes"></a><span data-ttu-id="e2c04-149">了解執行階段版本號碼變更</span><span class="sxs-lookup"><span data-stu-id="e2c04-149">Understand runtime version number changes</span></span>

<span data-ttu-id="e2c04-150">`MAJOR` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="e2c04-150">`MAJOR` is incremented when:</span></span>

* <span data-ttu-id="e2c04-151">產品或新產品方向發生重大便更。</span><span class="sxs-lookup"><span data-stu-id="e2c04-151">Significant changes occur to the product, or a new product direction.</span></span>
* <span data-ttu-id="e2c04-152">接受中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="e2c04-152">Breaking changes were taken.</span></span> <span data-ttu-id="e2c04-153">接受中斷性變更的標準較高。</span><span class="sxs-lookup"><span data-stu-id="e2c04-153">There's a high bar to accepting breaking changes.</span></span>
* <span data-ttu-id="e2c04-154">不再支援舊版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-154">An old version is no longer supported.</span></span>
* <span data-ttu-id="e2c04-155">採用現有相依性的較新 `MAJOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-155">A newer `MAJOR` version of an existing dependency is adopted.</span></span>

<span data-ttu-id="e2c04-156">`MINOR` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="e2c04-156">`MINOR` is incremented when:</span></span>

* <span data-ttu-id="e2c04-157">新增公用 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="e2c04-157">Public API surface area is added.</span></span>
* <span data-ttu-id="e2c04-158">新增新的行為。</span><span class="sxs-lookup"><span data-stu-id="e2c04-158">A new behavior is added.</span></span>
* <span data-ttu-id="e2c04-159">採用現有相依性的較新 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-159">A newer `MINOR` version of an existing dependency is adopted.</span></span>
* <span data-ttu-id="e2c04-160">引入新的相依性。</span><span class="sxs-lookup"><span data-stu-id="e2c04-160">A new dependency is introduced.</span></span>

<span data-ttu-id="e2c04-161">`PATCH` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="e2c04-161">`PATCH` is incremented when:</span></span>

* <span data-ttu-id="e2c04-162">已修正 Bug。</span><span class="sxs-lookup"><span data-stu-id="e2c04-162">Bug fixes are made.</span></span>
* <span data-ttu-id="e2c04-163">新增對較新平台的支援。</span><span class="sxs-lookup"><span data-stu-id="e2c04-163">Support for a newer platform is added.</span></span>
* <span data-ttu-id="e2c04-164">採用現有相依性的較新 `PATCH` 版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-164">A newer `PATCH` version of an existing dependency is adopted.</span></span>
* <span data-ttu-id="e2c04-165">任何其他不符合其中一個先前案例的變更。</span><span class="sxs-lookup"><span data-stu-id="e2c04-165">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="e2c04-166">當有多項變更時，因個別變更而影響的最高項目就會遞增，而下列項目會重設為零。</span><span class="sxs-lookup"><span data-stu-id="e2c04-166">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="e2c04-167">例如，當 `MAJOR` 遞增時，`MINOR` 和 `PATCH` 會重設為零。</span><span class="sxs-lookup"><span data-stu-id="e2c04-167">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="e2c04-168">當 `MINOR` 遞增時，`PATCH` 會重設為零而 `MAJOR` 保持不變。</span><span class="sxs-lookup"><span data-stu-id="e2c04-168">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

## <a name="version-numbers-in-file-names"></a><span data-ttu-id="e2c04-169">檔案名稱中的版本號碼</span><span class="sxs-lookup"><span data-stu-id="e2c04-169">Version numbers in file names</span></span>

<span data-ttu-id="e2c04-170">針對 .NET Core 下載的檔案具有版本，例如 `dotnet-sdk-2.1.300-win10-x64.exe`。</span><span class="sxs-lookup"><span data-stu-id="e2c04-170">The files downloaded for .NET Core carry the version, for example, `dotnet-sdk-2.1.300-win10-x64.exe`.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="e2c04-171">預覽版本</span><span class="sxs-lookup"><span data-stu-id="e2c04-171">Preview versions</span></span>

<span data-ttu-id="e2c04-172">預覽版本將 `-preview[number]-([build]|"final")` 附加至版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-172">Preview versions have a `-preview[number]-([build]|"final")` appended to the version.</span></span> <span data-ttu-id="e2c04-173">例如，`2.0.0-preview1-final`。</span><span class="sxs-lookup"><span data-stu-id="e2c04-173">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="e2c04-174">服務版本</span><span class="sxs-lookup"><span data-stu-id="e2c04-174">Servicing versions</span></span>

<span data-ttu-id="e2c04-175">版本發行之後，版本分支通常會停止產生每日組建，改為開始產生服務組建。</span><span class="sxs-lookup"><span data-stu-id="e2c04-175">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="e2c04-176">服務版本會將 `-servicing-[number]` 附加至版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-176">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="e2c04-177">例如，`2.0.1-servicing-006924`。</span><span class="sxs-lookup"><span data-stu-id="e2c04-177">For example, `2.0.1-servicing-006924`.</span></span>

## <a name="relationship-to-net-standard-versions"></a><span data-ttu-id="e2c04-178">與 .NET Standard 版本的關聯性</span><span class="sxs-lookup"><span data-stu-id="e2c04-178">Relationship to .NET Standard versions</span></span>

<span data-ttu-id="e2c04-179">.NET Standard 是由 .NET 參考組件所組成。</span><span class="sxs-lookup"><span data-stu-id="e2c04-179">.NET Standard consists of a .NET reference assembly.</span></span> <span data-ttu-id="e2c04-180">每個平台都有多個特定實作。</span><span class="sxs-lookup"><span data-stu-id="e2c04-180">There are multiple implementations specific to each platform.</span></span> <span data-ttu-id="e2c04-181">參考組件包含 .NET API 的定義，這是給定 .NET Standard 版本的一部分。</span><span class="sxs-lookup"><span data-stu-id="e2c04-181">The reference assembly contains the definition of .NET APIs which are part of a given .NET Standard version.</span></span> <span data-ttu-id="e2c04-182">每個實作都履行特定平台上的 .NET Standard 合約。</span><span class="sxs-lookup"><span data-stu-id="e2c04-182">Each implementation fulfills the .NET Standard contract on the specific platform.</span></span> <span data-ttu-id="e2c04-183">您可以在《.NET 指南》中的[.NET Standard](../../standard/net-standard.md) 一文深入了解 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="e2c04-183">You can learn more about .NET Standard in the article on [.NET Standard](../../standard/net-standard.md) in the .NET Guide.</span></span>

<span data-ttu-id="e2c04-184">.NET Standard 參考組件使用a `MAJOR.MINOR` 版本控制配置。</span><span class="sxs-lookup"><span data-stu-id="e2c04-184">The .NET Standard reference assembly uses a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="e2c04-185">`PATCH` 對 .NET Standard 而言不實用，因為它只公開 API 規格 (無實作)，而且根據定義，對 API 所做的任何變更都會代表未來集合中的變更，亦即新的 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-185">`PATCH` level isn't useful for .NET Standard because it exposes only an API specification (no implementation) and by definition any change to the API would represent a change in the feature set, and thus a new `MINOR` version.</span></span>

<span data-ttu-id="e2c04-186">可能可以更新每個平台上的實作，通常是做為平台發行版本的一部分，因此對在該平台上使用 .NET Standard 的開發人員而言並非顯而易見。</span><span class="sxs-lookup"><span data-stu-id="e2c04-186">The implementations on each platform may be updated, typically as part of the platform release, and thus not evident to the programmers using .NET Standard on that platform.</span></span>

<span data-ttu-id="e2c04-187">.NET Core 的每個版本都實作 .NET Standard. 的版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-187">Each version of .NET Core implements a version of .NET Standard.</span></span> <span data-ttu-id="e2c04-188">實作 .NET Standard 的版本意指支援舊版 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="e2c04-188">Implementing a version of .NET Standard implies support for previous versions of .NET Standard.</span></span> <span data-ttu-id="e2c04-189">.NET Standard 與 .NET Core 版本彼此獨立。</span><span class="sxs-lookup"><span data-stu-id="e2c04-189">.NET Standard and .NET Core version independently.</span></span> <span data-ttu-id="e2c04-190">.NET Core 2.0 實作 .NET Standard 2.0 只是巧合。</span><span class="sxs-lookup"><span data-stu-id="e2c04-190">It's a coincidence that .NET Core 2.0 implements .NET Standard 2.0.</span></span> <span data-ttu-id="e2c04-191">.NET Core 2.1 也實作 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="e2c04-191">.NET Core 2.1 also implements .NET Standard 2.0.</span></span> <span data-ttu-id="e2c04-192">.NET Core 將支援未來推出的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="e2c04-192">.NET Core will support future versions of .NET Standard as they become available.</span></span>

| <span data-ttu-id="e2c04-193">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e2c04-193">.NET Core</span></span> | <span data-ttu-id="e2c04-194">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e2c04-194">.NET Standard</span></span> |
|-----------|---------------|
| <span data-ttu-id="e2c04-195">1.0</span><span class="sxs-lookup"><span data-stu-id="e2c04-195">1.0</span></span>       | <span data-ttu-id="e2c04-196">最高到 1.6</span><span class="sxs-lookup"><span data-stu-id="e2c04-196">up to 1.6</span></span>     |
| <span data-ttu-id="e2c04-197">2.0</span><span class="sxs-lookup"><span data-stu-id="e2c04-197">2.0</span></span>       | <span data-ttu-id="e2c04-198">最高到 2.0</span><span class="sxs-lookup"><span data-stu-id="e2c04-198">up to 2.0</span></span>     |
| <span data-ttu-id="e2c04-199">2.1</span><span class="sxs-lookup"><span data-stu-id="e2c04-199">2.1</span></span>       | <span data-ttu-id="e2c04-200">最高到 2.0</span><span class="sxs-lookup"><span data-stu-id="e2c04-200">up to 2.0</span></span>     |

## <a name="see-also"></a><span data-ttu-id="e2c04-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2c04-201">See also</span></span>

* [<span data-ttu-id="e2c04-202">目標架構</span><span class="sxs-lookup"><span data-stu-id="e2c04-202">Target frameworks</span></span>](../../standard/frameworks.md)  
* [<span data-ttu-id="e2c04-203">.NET Core 發佈封裝</span><span class="sxs-lookup"><span data-stu-id="e2c04-203">.NET Core distribution packaging</span></span>](../build/distribution-packaging.md)  
* [<span data-ttu-id="e2c04-204">.NET Core 支援週期資料表</span><span class="sxs-lookup"><span data-stu-id="e2c04-204">.NET Core Support Lifecycle Fact Sheet</span></span>](https://www.microsoft.com/net/core/support)  
* <span data-ttu-id="e2c04-205">[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3) (.NET Core 2+ 版本繫結)</span><span class="sxs-lookup"><span data-stu-id="e2c04-205">[.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3)</span></span>  
* <span data-ttu-id="e2c04-206">[.NET Core 的 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="e2c04-206">[Docker images for .NET Core](https://hub.docker.com/r/microsoft/dotnet/)</span></span>
