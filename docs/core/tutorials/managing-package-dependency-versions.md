---
title: 如何管理 .NET Core 1.0 的套件相依性版本
description: 了解您的 .NET Core 程式庫和應用程式的套件相依性版本管理。
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
ms.workload:
- dotnetcore
ms.openlocfilehash: 2bb55f3bcd6678a127f099afbb9461cafe1a9c94
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a><span data-ttu-id="4dd80-104">如何管理 .NET Core 1.0 的套件相依性版本</span><span class="sxs-lookup"><span data-stu-id="4dd80-104">How to Manage Package Dependency Versions for .NET Core 1.0</span></span>

<span data-ttu-id="4dd80-105">本文章涵蓋您需要知道有關 .NET Core 程式庫和應用程式套件版本的資訊。</span><span class="sxs-lookup"><span data-stu-id="4dd80-105">This article covers what you need to know about package versions for your .NET Core libraries and apps.</span></span>

## <a name="glossary"></a><span data-ttu-id="4dd80-106">字彙表</span><span class="sxs-lookup"><span data-stu-id="4dd80-106">Glossary</span></span>

<span data-ttu-id="4dd80-107">**修正** - 修正相依性表示，您會使用在 NuGet 上發行、適用於 .NET Core 1.0 的相同系列套件。</span><span class="sxs-lookup"><span data-stu-id="4dd80-107">**Fix** - Fixing dependencies means you are using the same "family" of packages released on NuGet for .NET Core 1.0.</span></span>

<span data-ttu-id="4dd80-108">**中繼套件** - NuGet 套件，代表一組 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="4dd80-108">**Metapackage** - A NuGet package that represents a set of NuGet packages.</span></span>

<span data-ttu-id="4dd80-109">**修剪** - 從中繼套件移除不依賴之套件的動作。</span><span class="sxs-lookup"><span data-stu-id="4dd80-109">**Trimming** - The act of removing the packages you do not depend on from a metapackage.</span></span>  <span data-ttu-id="4dd80-110">這與 NuGet 套件作者有關。</span><span class="sxs-lookup"><span data-stu-id="4dd80-110">This is something relevant for NuGet package authors.</span></span>  <span data-ttu-id="4dd80-111">如需詳細資訊，請參閱[減少與 project.json 的套件相依性](../deploying/reducing-dependencies.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd80-111">See [Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md) for more information.</span></span> 

## <a name="fix-your-dependencies-to-net-core-10"></a><span data-ttu-id="4dd80-112">將相依性固定為 .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="4dd80-112">Fix your dependencies to .NET Core 1.0</span></span>

<span data-ttu-id="4dd80-113">若要可靠地還原套件，並撰寫可靠的程式碼，很重要的一點是將相依性固定為與 .NET Core 1.0 一起出貨的套件版本。</span><span class="sxs-lookup"><span data-stu-id="4dd80-113">To reliably restore packages and write reliable code, it's important that you fix your dependencies to the versions of packages shipping alongside .NET Core 1.0.</span></span>  <span data-ttu-id="4dd80-114">這表示每個套件應該有單一版本，而且不含任何額外的限定詞。</span><span class="sxs-lookup"><span data-stu-id="4dd80-114">This means every package should have a single version with no additional qualifiers.</span></span>

<span data-ttu-id="4dd80-115">**固定為 1.0 的套件範例**</span><span class="sxs-lookup"><span data-stu-id="4dd80-115">**Examples of packages fixed to 1.0**</span></span>

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

<span data-ttu-id="4dd80-116">**未固定為 1.0 的套件範例**</span><span class="sxs-lookup"><span data-stu-id="4dd80-116">**Examples of packages that are NOT fixed to 1.0**</span></span>

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a><span data-ttu-id="4dd80-117">這為什麼重要？</span><span class="sxs-lookup"><span data-stu-id="4dd80-117">Why does this matter?</span></span>

<span data-ttu-id="4dd80-118">我們保證，如果您將相依性固定為與 .NET Core 1.0 一起出貨的項目時，那些套件將一起運作。</span><span class="sxs-lookup"><span data-stu-id="4dd80-118">We guarantee that if you fix your dependencies to what ships alongside .NET Core 1.0, those packages will all work together.</span></span> <span data-ttu-id="4dd80-119">如果您使用未以此方式固定的套件，則沒有這種保證。</span><span class="sxs-lookup"><span data-stu-id="4dd80-119">There is no such guarantee if you use packages which aren't fixed in this way.</span></span>

### <a name="scenarios"></a><span data-ttu-id="4dd80-120">案例</span><span class="sxs-lookup"><span data-stu-id="4dd80-120">Scenarios</span></span>

<span data-ttu-id="4dd80-121">雖然與 .NET Core 1.0 一起發行的所有套件和其版本清單冗長，但如果您的程式碼落在特定狀況下，可能不必看完整份清單。</span><span class="sxs-lookup"><span data-stu-id="4dd80-121">Although there is a big list of all packages and their versions released with .NET Core 1.0, you may not have to look through it if your code falls under certain scenarios.</span></span>

<span data-ttu-id="4dd80-122">**您是否只依賴** `NETStandard.Library`**？**</span><span class="sxs-lookup"><span data-stu-id="4dd80-122">**Are you depending only on** `NETStandard.Library`**?**</span></span>

<span data-ttu-id="4dd80-123">如果是，您應該將 `NETStandard.Library` 套件固定為 `1.6` 版。</span><span class="sxs-lookup"><span data-stu-id="4dd80-123">If so, you should fix your `NETStandard.Library` package to version `1.6`.</span></span>  <span data-ttu-id="4dd80-124">因為這是策劃的中繼套件，其套件終止也會固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="4dd80-124">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="4dd80-125">**您是否只依賴** `Microsoft.NETCore.App`**？**</span><span class="sxs-lookup"><span data-stu-id="4dd80-125">**Are you depending only on** `Microsoft.NETCore.App`**?**</span></span>

<span data-ttu-id="4dd80-126">如果是，您應該將 `Microsoft.NETCore.App` 套件固定為 `1.0.0` 版。</span><span class="sxs-lookup"><span data-stu-id="4dd80-126">If so, you should fix your `Microsoft.NETCore.App` package to version `1.0.0`.</span></span>  <span data-ttu-id="4dd80-127">因為這是策劃的中繼套件，其套件終止也會固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="4dd80-127">Because this is a curated metapackage, its package closure is also fixed to 1.0.</span></span>

<span data-ttu-id="4dd80-128">**您是否[修剪](../deploying/reducing-dependencies.md)您的** `NETStandard.Library` **或** `Microsoft.NETCore.App` **中繼套件相依性？**</span><span class="sxs-lookup"><span data-stu-id="4dd80-128">**Are you [trimming](../deploying/reducing-dependencies.md) your** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackage dependencies?**</span></span>

<span data-ttu-id="4dd80-129">如果是，您應該確定您啟動用的中繼套件固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="4dd80-129">If so, you should ensure that the metapackage you start with is fixed to 1.0.</span></span>  <span data-ttu-id="4dd80-130">修剪之後依賴的個別套件也會固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="4dd80-130">The individual packages you depend on after trimming are also fixed to 1.0.</span></span>

<span data-ttu-id="4dd80-131">**您是否依賴** `NETStandard.Library` **或** `Microsoft.NETCore.App` **中繼套件之外的套件？**</span><span class="sxs-lookup"><span data-stu-id="4dd80-131">**Are you depending on packages outside the** `NETStandard.Library` **or** `Microsoft.NETCore.App` **metapackages?**</span></span>

<span data-ttu-id="4dd80-132">如果是，您需要將其他相依性固定為 1.0。</span><span class="sxs-lookup"><span data-stu-id="4dd80-132">If so, you need to fix your other dependencies to 1.0.</span></span>  <span data-ttu-id="4dd80-133">如需正確的套件版本和組建號碼，請參閱在本文結尾。</span><span class="sxs-lookup"><span data-stu-id="4dd80-133">See the correct package versions and build numbers at the end of this article.</span></span>

### <a name="a-note-on-using-a-splat-string--when-versioning"></a><span data-ttu-id="4dd80-134">版本控制時，使用 splat 字串 (\*) 的注意事項</span><span class="sxs-lookup"><span data-stu-id="4dd80-134">A note on using a splat string (\*) when versioning</span></span>

<span data-ttu-id="4dd80-135">您採用的版本控制模式可能是使用 splat (\*) 字串，就像這樣︰`"System.Collections":"4.0.11-*"`。</span><span class="sxs-lookup"><span data-stu-id="4dd80-135">You may have adopted a versioning pattern which uses a splat (\*) string like this: `"System.Collections":"4.0.11-*"`.</span></span>

<span data-ttu-id="4dd80-136">**您不應該這麼做**。</span><span class="sxs-lookup"><span data-stu-id="4dd80-136">**You should not do this**.</span></span>  <span data-ttu-id="4dd80-137">使用 splat 字串可能會導致從不同的組建還原套件，這些組建有些可能比 .NET Core 1.0 更遠。</span><span class="sxs-lookup"><span data-stu-id="4dd80-137">Using the splat string could result in restoring packages from different builds, some of which may be further along than .NET Core 1.0.</span></span>  <span data-ttu-id="4dd80-138">這可能導致某些套件不相容。</span><span class="sxs-lookup"><span data-stu-id="4dd80-138">This could then result in some packages being incompatible.</span></span>

## <a name="packages-and-version-numbers-organized-by-metapackage"></a><span data-ttu-id="4dd80-139">依中繼套件組織的套件和版本號碼</span><span class="sxs-lookup"><span data-stu-id="4dd80-139">Packages and Version Numbers organized by Metapackage</span></span>

<span data-ttu-id="4dd80-140">[所有 .NET Standard 套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="4dd80-140">[List of all .NET Standard packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).</span></span>

<span data-ttu-id="4dd80-141">[所有執行階段套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="4dd80-141">[List of all runtime packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).</span></span>

<span data-ttu-id="4dd80-142">[所有 .NET Core 應用程式套件和其適用於 1.0 的版本清單](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt)。</span><span class="sxs-lookup"><span data-stu-id="4dd80-142">[List of all .NET Core application packages and their versions for 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).</span></span>
