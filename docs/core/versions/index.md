---
title: .NET 執行時間和 SDK 的版本設定方式
description: 本文說明如何將 .NET SDK 和執行時間的版本設定 (類似于語義版本設定) 。
ms.date: 12/07/2020
ms.openlocfilehash: 2fbc2775f31b4eab1c9883282c58accd9bb2b9f5
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633620"
---
# <a name="overview-of-how-net-is-versioned"></a><span data-ttu-id="b9f2a-103">.NET 的版本設定總覽</span><span class="sxs-lookup"><span data-stu-id="b9f2a-103">Overview of how .NET is versioned</span></span>

<span data-ttu-id="b9f2a-104">[.Net 執行時間和 .NET SDK](../introduction.md#sdk-and-runtimes)會以不同的頻率新增新功能。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-104">The [.NET Runtime and the .NET SDK](../introduction.md#sdk-and-runtimes) add new features at different frequencies.</span></span> <span data-ttu-id="b9f2a-105">一般來說，SDK 的更新頻率會比執行時間更頻繁。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-105">In general, the SDK is updated more frequently than the Runtime.</span></span> <span data-ttu-id="b9f2a-106">本文說明執行時間和 SDK 版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-106">This article explains the runtime and the SDK version numbers.</span></span>

## <a name="versioning-details"></a><span data-ttu-id="b9f2a-107">版本控制的詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9f2a-107">Versioning details</span></span>

<span data-ttu-id="b9f2a-108">.NET 執行時間有一種主要/次要/修補方法，可進行遵循 [語義版本](#semantic-versioning)控制的版本控制。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-108">The .NET Runtime has a major/minor/patch approach to versioning that follows [semantic versioning](#semantic-versioning).</span></span>

<span data-ttu-id="b9f2a-109">.NET SDK 不遵循語義版本控制。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-109">The .NET SDK doesn't follow semantic versioning.</span></span> <span data-ttu-id="b9f2a-110">.NET SDK 的發行速度更快，而且其版本號碼必須傳達對齊的執行時間和 SDK 本身的次要和修補程式版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-110">The .NET SDK releases faster and its version numbers must communicate both the aligned runtime and the SDK's own minor and patch releases.</span></span>

<span data-ttu-id="b9f2a-111">.NET SDK 版本號碼的前兩個位置會鎖定至其發行的 .NET 執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-111">The first two positions of the .NET SDK version number are locked to the .NET Runtime version it released with.</span></span> <span data-ttu-id="b9f2a-112">SDK 的每個版本都可以針對此執行階段或任何較低的版本建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-112">Each version of the SDK can create applications for this runtime or any lower version.</span></span>

<span data-ttu-id="b9f2a-113">SDK 版本號碼的第三個位置同時傳達次要與修補號碼。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-113">The third position of the SDK version number communicates both the minor and patch number.</span></span> <span data-ttu-id="b9f2a-114">次要版本會被乘以 100。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-114">The minor version is multiplied by 100.</span></span> <span data-ttu-id="b9f2a-115">最後兩位數代表修補號碼。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-115">The final two digits represent the patch number.</span></span> <span data-ttu-id="b9f2a-116">次要版本 1、修補版本 2 將以 102 表示。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-116">Minor version 1, patch version 2 would be represented as 102.</span></span> <span data-ttu-id="b9f2a-117">例如，以下是執行時間和 SDK 版本號碼的可能順序：</span><span class="sxs-lookup"><span data-stu-id="b9f2a-117">For example, here's a possible sequence of runtime and SDK version numbers:</span></span>

| <span data-ttu-id="b9f2a-118">變更</span><span class="sxs-lookup"><span data-stu-id="b9f2a-118">Change</span></span>                | <span data-ttu-id="b9f2a-119">.NET 執行階段</span><span class="sxs-lookup"><span data-stu-id="b9f2a-119">.NET Runtime</span></span>      | <span data-ttu-id="b9f2a-120">.NET SDK (\*) </span><span class="sxs-lookup"><span data-stu-id="b9f2a-120">.NET SDK (\*)</span></span>     |
|-----------------------|-------------------|-------------------|
| <span data-ttu-id="b9f2a-121">初始版本</span><span class="sxs-lookup"><span data-stu-id="b9f2a-121">Initial release</span></span>       | <span data-ttu-id="b9f2a-122">2.2.0</span><span class="sxs-lookup"><span data-stu-id="b9f2a-122">2.2.0</span></span>             | <span data-ttu-id="b9f2a-123">2.2.100</span><span class="sxs-lookup"><span data-stu-id="b9f2a-123">2.2.100</span></span>           |
| <span data-ttu-id="b9f2a-124">SDK 修補程式</span><span class="sxs-lookup"><span data-stu-id="b9f2a-124">SDK patch</span></span>             | <span data-ttu-id="b9f2a-125">2.2.0</span><span class="sxs-lookup"><span data-stu-id="b9f2a-125">2.2.0</span></span>             | <span data-ttu-id="b9f2a-126">2.2.101</span><span class="sxs-lookup"><span data-stu-id="b9f2a-126">2.2.101</span></span>           |
| <span data-ttu-id="b9f2a-127">執行時間和 SDK 修補程式</span><span class="sxs-lookup"><span data-stu-id="b9f2a-127">Runtime and SDK patch</span></span> | <span data-ttu-id="b9f2a-128">2.2.1</span><span class="sxs-lookup"><span data-stu-id="b9f2a-128">2.2.1</span></span>             | <span data-ttu-id="b9f2a-129">2.2.102</span><span class="sxs-lookup"><span data-stu-id="b9f2a-129">2.2.102</span></span>           |
| <span data-ttu-id="b9f2a-130">SDK 功能變更</span><span class="sxs-lookup"><span data-stu-id="b9f2a-130">SDK feature change</span></span>    | <span data-ttu-id="b9f2a-131">2.2.1</span><span class="sxs-lookup"><span data-stu-id="b9f2a-131">2.2.1</span></span>             | <span data-ttu-id="b9f2a-132">2.2.200</span><span class="sxs-lookup"><span data-stu-id="b9f2a-132">2.2.200</span></span>           |

<span data-ttu-id="b9f2a-133">注意：</span><span class="sxs-lookup"><span data-stu-id="b9f2a-133">NOTES:</span></span>

- <span data-ttu-id="b9f2a-134">若 SDK 在執行階段功能更新之前有 10 個功能更新，版本號碼會滾入 1000 系列，且具有 2.2.1000 做為 2.2.900 之後的未來發行版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-134">If the SDK has 10 feature updates before a runtime feature update, version numbers roll into the 1000 series with numbers like 2.2.1000 as the feature release following 2.2.900.</span></span> <span data-ttu-id="b9f2a-135">此情況不應該發生。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-135">This situation isn't expected to occur.</span></span>
- <span data-ttu-id="b9f2a-136">不會發生沒有功能發行版本的 99 修補發行版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-136">99 patch releases without a feature release won't occur.</span></span> <span data-ttu-id="b9f2a-137">若發行版本接近此號碼，它會強制功能發行版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-137">If a release approaches this number, it forces a feature release.</span></span>

<span data-ttu-id="b9f2a-138">您可以在 [dotnet/designs](https://github.com/dotnet/designs/pull/29) 存放庫 \(英文\) 中查看此初始提案的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-138">You can see more details in the initial proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="b9f2a-139">語意化版本控制系統</span><span class="sxs-lookup"><span data-stu-id="b9f2a-139">Semantic versioning</span></span>

<span data-ttu-id="b9f2a-140">.NET *運行* 時間大致符合 [語義版本控制 (SemVer)](https://semver.org/)，採用 `MAJOR.MINOR.PATCH` 版本控制的不同部分來描述變更的程度和類型，以使用版本控制。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-140">The .NET *Runtime* roughly adheres to [Semantic Versioning (SemVer)](https://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="b9f2a-141">選擇性的 `PRERELEASE` 和 `BUILDNUMBER` 組件絕對不會是受支援版本的一部分，並只會存在於每日組建、來自來源目標的本機組建，以及未支援的預覽版本上。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-141">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="understand-runtime-version-number-changes"></a><span data-ttu-id="b9f2a-142">了解執行階段版本號碼變更</span><span class="sxs-lookup"><span data-stu-id="b9f2a-142">Understand runtime version number changes</span></span>

<span data-ttu-id="b9f2a-143">`MAJOR` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="b9f2a-143">`MAJOR` is incremented when:</span></span>

- <span data-ttu-id="b9f2a-144">產品或新產品方向發生重大便更。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-144">Significant changes occur to the product, or a new product direction.</span></span>
- <span data-ttu-id="b9f2a-145">接受中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-145">Breaking changes were taken.</span></span> <span data-ttu-id="b9f2a-146">接受中斷性變更的標準較高。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-146">There's a high bar to accepting breaking changes.</span></span>
- <span data-ttu-id="b9f2a-147">不再支援舊版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-147">An old version is no longer supported.</span></span>
- <span data-ttu-id="b9f2a-148">採用現有相依性的較新 `MAJOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-148">A newer `MAJOR` version of an existing dependency is adopted.</span></span>

<span data-ttu-id="b9f2a-149">`MINOR` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="b9f2a-149">`MINOR` is incremented when:</span></span>

- <span data-ttu-id="b9f2a-150">新增公用 API 介面區。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-150">Public API surface area is added.</span></span>
- <span data-ttu-id="b9f2a-151">新增新的行為。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-151">A new behavior is added.</span></span>
- <span data-ttu-id="b9f2a-152">採用現有相依性的較新 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-152">A newer `MINOR` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="b9f2a-153">引入新的相依性。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-153">A new dependency is introduced.</span></span>

<span data-ttu-id="b9f2a-154">`PATCH` 的遞增時機為：</span><span class="sxs-lookup"><span data-stu-id="b9f2a-154">`PATCH` is incremented when:</span></span>

- <span data-ttu-id="b9f2a-155">已修正 Bug。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-155">Bug fixes are made.</span></span>
- <span data-ttu-id="b9f2a-156">新增對較新平台的支援。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-156">Support for a newer platform is added.</span></span>
- <span data-ttu-id="b9f2a-157">採用現有相依性的較新 `PATCH` 版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-157">A newer `PATCH` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="b9f2a-158">任何其他不符合其中一個先前案例的變更。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-158">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="b9f2a-159">當有多項變更時，因個別變更而影響的最高項目就會遞增，而下列項目會重設為零。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-159">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="b9f2a-160">例如，當 `MAJOR` 遞增時，`MINOR` 和 `PATCH` 會重設為零。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-160">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="b9f2a-161">當 `MINOR` 遞增時，`PATCH` 會重設為零而 `MAJOR` 保持不變。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-161">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

## <a name="version-numbers-in-file-names"></a><span data-ttu-id="b9f2a-162">檔案名稱中的版本號碼</span><span class="sxs-lookup"><span data-stu-id="b9f2a-162">Version numbers in file names</span></span>

<span data-ttu-id="b9f2a-163">針對 .NET 下載的檔案會包含版本，例如 `dotnet-sdk-2.1.300-win10-x64.exe` 。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-163">The files downloaded for .NET carry the version, for example, `dotnet-sdk-2.1.300-win10-x64.exe`.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="b9f2a-164">預覽版本</span><span class="sxs-lookup"><span data-stu-id="b9f2a-164">Preview versions</span></span>

<span data-ttu-id="b9f2a-165">預覽版本已 `-preview[number]-([build]|"final")` 附加至版本號碼。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-165">Preview versions have a `-preview[number]-([build]|"final")` appended to the version number.</span></span> <span data-ttu-id="b9f2a-166">例如： `2.0.0-preview1-final` 。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-166">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="b9f2a-167">服務版本</span><span class="sxs-lookup"><span data-stu-id="b9f2a-167">Servicing versions</span></span>

<span data-ttu-id="b9f2a-168">版本發行之後，版本分支通常會停止產生每日組建，改為開始產生服務組建。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-168">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="b9f2a-169">服務版本會將 `-servicing-[number]` 附加至版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-169">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="b9f2a-170">例如： `2.0.1-servicing-006924` 。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-170">For example, `2.0.1-servicing-006924`.</span></span>

## <a name="relationship-to-net-standard-versions"></a><span data-ttu-id="b9f2a-171">與 .NET Standard 版本的關聯性</span><span class="sxs-lookup"><span data-stu-id="b9f2a-171">Relationship to .NET Standard versions</span></span>

<span data-ttu-id="b9f2a-172">.NET Standard 是由 .NET 參考組件所組成。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-172">.NET Standard consists of a .NET reference assembly.</span></span> <span data-ttu-id="b9f2a-173">每個平台都有多個特定實作。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-173">There are multiple implementations specific to each platform.</span></span> <span data-ttu-id="b9f2a-174">參考組件包含 .NET API 的定義，這是給定 .NET Standard 版本的一部分。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-174">The reference assembly contains the definition of .NET APIs which are part of a given .NET Standard version.</span></span> <span data-ttu-id="b9f2a-175">每個實作都履行特定平台上的 .NET Standard 合約。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-175">Each implementation fulfills the .NET Standard contract on the specific platform.</span></span>

<span data-ttu-id="b9f2a-176">.NET Standard 參考組件使用a `MAJOR.MINOR` 版本控制配置。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-176">The .NET Standard reference assembly uses a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="b9f2a-177">`PATCH` 對 .NET Standard 而言不實用，因為它只公開 API 規格 (無實作)，而且根據定義，對 API 所做的任何變更都會代表未來集合中的變更，亦即新的 `MINOR` 版本。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-177">`PATCH` level isn't useful for .NET Standard because it exposes only an API specification (no implementation) and by definition any change to the API would represent a change in the feature set, and thus a new `MINOR` version.</span></span>

<span data-ttu-id="b9f2a-178">可能可以更新每個平台上的實作，通常是做為平台發行版本的一部分，因此對在該平台上使用 .NET Standard 的開發人員而言並非顯而易見。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-178">The implementations on each platform may be updated, typically as part of the platform release, and thus not evident to the programmers using .NET Standard on that platform.</span></span>

<span data-ttu-id="b9f2a-179">如需詳細資訊，請參閱 [.NET Standard](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="b9f2a-179">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9f2a-180">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9f2a-180">See also</span></span>

- [<span data-ttu-id="b9f2a-181">目標架構</span><span class="sxs-lookup"><span data-stu-id="b9f2a-181">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="b9f2a-182">.NET 散發封裝</span><span class="sxs-lookup"><span data-stu-id="b9f2a-182">.NET distribution packaging</span></span>](../distribution-packaging.md)
- [<span data-ttu-id="b9f2a-183">.NET 支援週期的事實表</span><span class="sxs-lookup"><span data-stu-id="b9f2a-183">.NET Support Lifecycle Fact Sheet</span></span>](https://dotnet.microsoft.com/platform/support/policy)
- [<span data-ttu-id="b9f2a-184">適用于 .NET 的 Docker 映射</span><span class="sxs-lookup"><span data-stu-id="b9f2a-184">Docker images for .NET</span></span>](https://hub.docker.com/_/microsoft-dotnet/)
