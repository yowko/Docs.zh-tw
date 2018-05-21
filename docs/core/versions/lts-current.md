---
title: .NET Core 支援
description: 了解適用於 .NET Core 的不同版本序列的支援 (LTS 和目前)
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.openlocfilehash: b61aa48451cee60be4968c151b97746a3aef85c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-support"></a><span data-ttu-id="b189b-103">.NET Core 支援</span><span class="sxs-lookup"><span data-stu-id="b189b-103">.NET Core Support</span></span>

<span data-ttu-id="b189b-104">這是 .NET Core 支援的一般說明。</span><span class="sxs-lookup"><span data-stu-id="b189b-104">This is a general description of .NET Core support.</span></span>

## <a name="lts-and-current-release-trains"></a><span data-ttu-id="b189b-105">LTS 和目前的 Release Train</span><span class="sxs-lookup"><span data-stu-id="b189b-105">LTS and Current Release Trains</span></span>

<span data-ttu-id="b189b-106">支援兩個 Release Train 是整個軟體界常用的概念，特別是像 .NET Core 這類開放原始碼專案。</span><span class="sxs-lookup"><span data-stu-id="b189b-106">Having two support release trains is a common concept in use throughout the software world, specially for open-source projects like .NET Core.</span></span> <span data-ttu-id="b189b-107">.NET Core 支援下列版本序列︰[長期支援 (LTS) (英文)](https://en.wikipedia.org/wiki/Long-term_support) 和目前。</span><span class="sxs-lookup"><span data-stu-id="b189b-107">.NET Core has the following support release trains: [Long Term Support (LTS)](https://en.wikipedia.org/wiki/Long-term_support) and Current.</span></span> <span data-ttu-id="b189b-108">LTS 版本會受到維護，以在其週期內提供穩定性，可接收重要問題的修正和安全性問題修正。</span><span class="sxs-lookup"><span data-stu-id="b189b-108">LTS releases are maintained for stability over their lifecycle, receiving fixes for important issues and security fixes.</span></span> <span data-ttu-id="b189b-109">目前版本中會有新的功能工作和其他 Bug 修正。</span><span class="sxs-lookup"><span data-stu-id="b189b-109">New feature work and additional bug fixes take place in Current releases.</span></span> <span data-ttu-id="b189b-110">從支援的觀點來看，這些 Release Train 具有下列支援週期屬性。</span><span class="sxs-lookup"><span data-stu-id="b189b-110">From a support perspective, these release trains have the following support lifecycle attributes.</span></span>

<span data-ttu-id="b189b-111">LTS 版本</span><span class="sxs-lookup"><span data-stu-id="b189b-111">LTS releases are</span></span>
* <span data-ttu-id="b189b-112">可於 LTS 版本全面上市後，提供為期三年的支援</span><span class="sxs-lookup"><span data-stu-id="b189b-112">Supported for three years after the general availability date of a LTS release</span></span>
* <span data-ttu-id="b189b-113">或可於後續的 LTS 版本全面上市後，提供為期一年的支援</span><span class="sxs-lookup"><span data-stu-id="b189b-113">Or one year after the general availability of a subsequent LTS release</span></span>

<span data-ttu-id="b189b-114">目前版本</span><span class="sxs-lookup"><span data-stu-id="b189b-114">Current releases are</span></span>
* <span data-ttu-id="b189b-115">和父代 LTS 版本一樣，同樣提供為期三年的支援</span><span class="sxs-lookup"><span data-stu-id="b189b-115">Supported within the same three-year window as the parent LTS release</span></span>
* <span data-ttu-id="b189b-116">可於後續的目前版本全面上市後，提供為期三個月的支援</span><span class="sxs-lookup"><span data-stu-id="b189b-116">Supported for three months after the general availability of a subsequent Current release</span></span>
* <span data-ttu-id="b189b-117">並可於後續的 LTS 版本全面上市後，提供為期一年的支援</span><span class="sxs-lookup"><span data-stu-id="b189b-117">And one year after the general availability of a subsequent LTS release</span></span>

## <a name="versioning"></a><span data-ttu-id="b189b-118">版本控制</span><span class="sxs-lookup"><span data-stu-id="b189b-118">Versioning</span></span>
<span data-ttu-id="b189b-119">利用增加的主要版本號碼來標示新的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="b189b-119">New LTS releases are marked by an increase in the Major version number.</span></span> <span data-ttu-id="b189b-120">目前版本的主要版本號碼會和對應的 LTS Train 相同，並會利用增加的主要版本號碼來標示版本。</span><span class="sxs-lookup"><span data-stu-id="b189b-120">Current releases have the same Major number as the corresponding LTS train and are marked by an increase in the Minor version number.</span></span> <span data-ttu-id="b189b-121">例如，1.0.3 為 LTS 版本，而 1.1.0 則為目前版本。</span><span class="sxs-lookup"><span data-stu-id="b189b-121">For example, 1.0.3 would be LTS and 1.1.0 would be Current.</span></span> <span data-ttu-id="b189b-122">對任一 Train 更新 Bug 修正，會讓修補檔案版本遞增。</span><span class="sxs-lookup"><span data-stu-id="b189b-122">Bug fix updates to either train increment the Patch version.</span></span> <span data-ttu-id="b189b-123">如需版本控制配置的詳細資訊，請參閱 [.NET Core 版本控制](index.md)。</span><span class="sxs-lookup"><span data-stu-id="b189b-123">For more information on the versioning scheme, see [.NET Core Versioning](index.md).</span></span>

## <a name="what-causes-updates-in-lts-and-current-trains"></a><span data-ttu-id="b189b-124">在 LTS 和目前的 Train 中造成更新的原因為何？</span><span class="sxs-lookup"><span data-stu-id="b189b-124">What causes updates in LTS and Current trains?</span></span>
<span data-ttu-id="b189b-125">若要了解哪些特定變更，例如 Bug 修正或加入 API，會導致更新版本號碼，請檢閱[版本控制說明文件](index.md)中的「決策樹」一節。</span><span class="sxs-lookup"><span data-stu-id="b189b-125">To understand what specific changes, such as bug fixes or the addition of APIs, cause updates to the version numbers review the Decision Tree section in the [Versioning Documentation](index.md).</span></span> <span data-ttu-id="b189b-126">要決定將哪些變更從目前版本提取到 LTS 分支中，並沒有黃金規則。</span><span class="sxs-lookup"><span data-stu-id="b189b-126">There is not a golden set of rules that decide what changes are pulled into the LTS branch from Current.</span></span> <span data-ttu-id="b189b-127">一般而言，可修正預期行為的必要安全性問題更新與修補檔案，都會造成更新 LTS 分支。</span><span class="sxs-lookup"><span data-stu-id="b189b-127">Typically, necessary security updates and patches that fix expected behaviour are reasons to update the LTS branch.</span></span> <span data-ttu-id="b189b-128">雖然這不一定可行，但我們也想要支援 LTS 分支上最近的桌面開發人員作業系統。</span><span class="sxs-lookup"><span data-stu-id="b189b-128">We also intend to support recent desktop developer operating systems on the LTS branch, though this may not always be possible.</span></span> <span data-ttu-id="b189b-129">想要掌握特定版本中支援哪些 API、修正及作業系統，最好瀏覽其在 GitHub 上的[版本資訊](https://github.com/dotnet/core/tree/master/release-notes)。</span><span class="sxs-lookup"><span data-stu-id="b189b-129">A good way to catch up on what APIs, fixes, and operating systems are supported in a certain release is to browse its [release notes](https://github.com/dotnet/core/tree/master/release-notes) on GitHub.</span></span>

### <a name="further-reading"></a><span data-ttu-id="b189b-130">進一步閱讀</span><span class="sxs-lookup"><span data-stu-id="b189b-130">Further Reading</span></span>
* [<span data-ttu-id="b189b-131">.NET Core 支援週期資料表</span><span class="sxs-lookup"><span data-stu-id="b189b-131">.NET Core Support Lifecycle Fact Sheet</span></span>](https://www.microsoft.com/net/core/support)
* [<span data-ttu-id="b189b-132">目前支援的作業系統和版本</span><span class="sxs-lookup"><span data-stu-id="b189b-132">Currently supported operating systems and versions</span></span>](https://github.com/dotnet/core/blob/master/roadmap.md)
