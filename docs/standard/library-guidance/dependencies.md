---
title: 相依性與 .NET 程式庫
description: 在 .NET 程式庫中管理 NuGet 相依性的最佳做法建議。
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 5566ab83040ce5dc23520401e3fc4bb619af4ec4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909917"
---
# <a name="dependencies"></a><span data-ttu-id="fd452-103">相依性</span><span class="sxs-lookup"><span data-stu-id="fd452-103">Dependencies</span></span>

<span data-ttu-id="fd452-104">將相依性新增至 .NET 程式庫的主要方式是參考 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="fd452-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="fd452-105">雖然 NuGet 套件參考能讓您快速地重複使用並運用已撰寫的功能，但它們也是造成 .NET 開發人員間摩擦的常見原因。</span><span class="sxs-lookup"><span data-stu-id="fd452-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="fd452-106">若要避免在其他 .NET 程式庫中所做的變更造成您的 .NET 程式庫中斷 (反之亦然)，正確地管理相依性便顯得非常重要！</span><span class="sxs-lookup"><span data-stu-id="fd452-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="fd452-107">菱形相依性</span><span class="sxs-lookup"><span data-stu-id="fd452-107">Diamond dependencies</span></span>

<span data-ttu-id="fd452-108">.NET 專案在其相依性樹狀結構中經常會有相同套件的多個版本。</span><span class="sxs-lookup"><span data-stu-id="fd452-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="fd452-109">例如，某個應用程式會相依於兩個 NuGet 套件，而每個套件都會相依於相同套件的不同版本。</span><span class="sxs-lookup"><span data-stu-id="fd452-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="fd452-110">這使得應用程式的相依性關係圖中存在菱形相依性。</span><span class="sxs-lookup"><span data-stu-id="fd452-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="fd452-111">![菱形相依性](./media/dependencies/diamond-dependency.png "菱形相依性")</span><span class="sxs-lookup"><span data-stu-id="fd452-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="fd452-112">在建置期間，NuGet 會分析專案相依的所有套件，包含相依性的相依性。</span><span class="sxs-lookup"><span data-stu-id="fd452-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="fd452-113">偵測到相同套件的多個版本時，系統會評估規則以從中挑選。</span><span class="sxs-lookup"><span data-stu-id="fd452-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="fd452-114">整合套件是必要的，因為在相同的應用程式中同時執行某個組件的多個版本，勢必會在 .NET 中產生問題。</span><span class="sxs-lookup"><span data-stu-id="fd452-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="fd452-115">雖然大部分的菱形相依性都很容易解決，但它們可能會在某些情況下造成問題：</span><span class="sxs-lookup"><span data-stu-id="fd452-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="fd452-116">**衝突的 NuGet 套件參考**會防止系統在套件還原期間解析某個版本。</span><span class="sxs-lookup"><span data-stu-id="fd452-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="fd452-117">**版本之間的中斷性變更**會在執行階段造成錯誤和例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fd452-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="fd452-118">**套件組件具有強式名稱**、組件版本已變更，且應用程式是在 .NET Framework 上執行。</span><span class="sxs-lookup"><span data-stu-id="fd452-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="fd452-119">需要進行組件繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="fd452-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="fd452-120">您不可能得知其他人會將您的套件搭配哪些套件使用。</span><span class="sxs-lookup"><span data-stu-id="fd452-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="fd452-121">一個降低菱形相依性中斷您程式庫之機會的良好方式，便是將您所相依之套件的數目降到最低。</span><span class="sxs-lookup"><span data-stu-id="fd452-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="fd452-122">**✔️ 請務必**檢閱您的 .NET 程式庫，以找出非必要的相依性。</span><span class="sxs-lookup"><span data-stu-id="fd452-122">**✔️ DO** review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="fd452-123">NuGet 相依性版本範圍</span><span class="sxs-lookup"><span data-stu-id="fd452-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="fd452-124">套件參考能指定其所允許之有效套件的範圍。</span><span class="sxs-lookup"><span data-stu-id="fd452-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="fd452-125">通常，專案檔案中的套件參考版本指的是最小版本，且沒有最大版本。</span><span class="sxs-lookup"><span data-stu-id="fd452-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="fd452-126">NuGet 用來解決相依性的規則非常[複雜](/nuget/consume-packages/dependency-resolution)，但 NuGet 一律會尋找最低的適用版本。</span><span class="sxs-lookup"><span data-stu-id="fd452-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="fd452-127">NuGet 之所以會偏好使用最低適用版本，而非最高版本的原因，是因為最低版本的相容性問題最少。</span><span class="sxs-lookup"><span data-stu-id="fd452-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="fd452-128">基於 NuGet 的最低適用版本規則，我們並不需要在套件參考上放置較高版本或確切範圍來避免取得最新的版本。</span><span class="sxs-lookup"><span data-stu-id="fd452-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="fd452-129">因為 NuGet 已經會嘗試為您找出最低且最具相容性的版本。</span><span class="sxs-lookup"><span data-stu-id="fd452-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="fd452-130">較高版本限制會在發生衝突時造成 NuGet 失敗。</span><span class="sxs-lookup"><span data-stu-id="fd452-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="fd452-131">例如，某個程式庫僅接受 1.0 版，而另一個程式庫則需要 2.0 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="fd452-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="fd452-132">雖然 2.0 版可能會出現中斷性變更，嚴格或較高限制版本相依性將一定會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="fd452-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="fd452-133">![菱形相依性衝突](./media/dependencies/diamond-dependency-conflict.png "菱形相依性衝突")</span><span class="sxs-lookup"><span data-stu-id="fd452-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="fd452-134">**❌ 請勿**使用沒有最小版本的 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="fd452-134">**❌ DO NOT** have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="fd452-135">**❌ 避免**要求明確版本的 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="fd452-135">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="fd452-136">**❌ 請避免**使用具有版本較高限制的 NuGet 套件參考。</span><span class="sxs-lookup"><span data-stu-id="fd452-136">**❌ AVOID** NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="fd452-137">NuGet 共用的來源套件</span><span class="sxs-lookup"><span data-stu-id="fd452-137">NuGet shared source packages</span></span>

<span data-ttu-id="fd452-138">其中一個降低外部 NuGet 套件相依性的方式，是參考共用的來源套件。</span><span class="sxs-lookup"><span data-stu-id="fd452-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="fd452-139">共用的來源套件包含[原始程式碼檔案](/nuget/reference/nuspec#including-content-files)，這些檔案會在被參考時包含在專案中。</span><span class="sxs-lookup"><span data-stu-id="fd452-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="fd452-140">因為您只是包含與專案其餘部分一起編譯的原始程式碼檔案，所以不會有任何外部相依性，也不會有發生衝突的機會。</span><span class="sxs-lookup"><span data-stu-id="fd452-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="fd452-141">共用的來源套件很適合用來包含較小的功能片段。</span><span class="sxs-lookup"><span data-stu-id="fd452-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="fd452-142">例如，適用於進行 HTTP 呼叫之協助程式的共用來源套件。</span><span class="sxs-lookup"><span data-stu-id="fd452-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="fd452-143">![共用的來源套件](./media/dependencies/shared-source-package.png "共用的來源套件")</span><span class="sxs-lookup"><span data-stu-id="fd452-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="fd452-144">![共用的來源專案](./media/dependencies/shared-source-project.png "共用的來源專案")</span><span class="sxs-lookup"><span data-stu-id="fd452-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="fd452-145">共用的來源套件有一些限制。</span><span class="sxs-lookup"><span data-stu-id="fd452-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="fd452-146">它們只能由 `PackageReference` 參考，因此會排除較舊的 `packages.config` 專案。</span><span class="sxs-lookup"><span data-stu-id="fd452-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="fd452-147">此外，共用的來源套件只適用於具有相同語言類型的專案。</span><span class="sxs-lookup"><span data-stu-id="fd452-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="fd452-148">因為這些限制，共用的來源套件最適合在開放原始碼專案內共用功能時使用。</span><span class="sxs-lookup"><span data-stu-id="fd452-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="fd452-149">**✔️ 請考慮**針對較小的內部功能片段使用共用的來源套件。</span><span class="sxs-lookup"><span data-stu-id="fd452-149">**✔️ CONSIDER** referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="fd452-150">**✔️ 請考慮**在套件提供的是較小的內部功能片段的情況下，使它成為共用的來源套件。</span><span class="sxs-lookup"><span data-stu-id="fd452-150">**✔️ CONSIDER** making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="fd452-151">**✔️ 請務必**搭配 `PrivateAssets="All"` 參考共用的來源套件。</span><span class="sxs-lookup"><span data-stu-id="fd452-151">**✔️ DO** reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="fd452-152">此設定能告訴 NuGet 該套件僅適用於開發階段，且不應該公開為公用相依性。</span><span class="sxs-lookup"><span data-stu-id="fd452-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="fd452-153">**❌ 請勿**在您的公用 API 中包含共用的來源套件類型。</span><span class="sxs-lookup"><span data-stu-id="fd452-153">**❌ DO NOT** have shared source package types in your public API.</span></span>

> <span data-ttu-id="fd452-154">共用來源類型會編譯為參考組件，且不能跨越組件界線進行交換。</span><span class="sxs-lookup"><span data-stu-id="fd452-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="fd452-155">例如，某個專案中的共用來源 `IRepository` 類型，與另一個專案中相同的共用來源 `IRepository` 將會是完全不同的類型。</span><span class="sxs-lookup"><span data-stu-id="fd452-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="fd452-156">共用來源套件中的類型應該僅具有 `internal` 可見性。</span><span class="sxs-lookup"><span data-stu-id="fd452-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="fd452-157">**❌ 請勿**將共用的來源套件發佈至 NuGet.org。</span><span class="sxs-lookup"><span data-stu-id="fd452-157">**❌ DO NOT** publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="fd452-158">共用的來源套件包含原始程式碼，而且只能用於具有相同語言類型的專案。</span><span class="sxs-lookup"><span data-stu-id="fd452-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="fd452-159">例如，以 F# 撰寫的應用程式將無法使用以 C# 撰寫的共用來源套件。</span><span class="sxs-lookup"><span data-stu-id="fd452-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="fd452-160">將共用原始碼套件發佈至[本機摘要或 MyGet](./publish-nuget-package.md)，以在專案內部取用它們。</span><span class="sxs-lookup"><span data-stu-id="fd452-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fd452-161">[上一頁](nuget.md)
>[下一頁](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="fd452-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
