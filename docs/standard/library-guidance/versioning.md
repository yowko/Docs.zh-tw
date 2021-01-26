---
title: 版本控制與 .NET 程式庫
description: .NET 程式庫版本控制的最佳做法建議。
ms.date: 01/26/2021
ms.openlocfilehash: 1f3a14a7c32091621dda30a2d86724915d629564
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794723"
---
# <a name="versioning"></a><span data-ttu-id="d84f0-103">版本控制</span><span class="sxs-lookup"><span data-stu-id="d84f0-103">Versioning</span></span>

<span data-ttu-id="d84f0-104">軟體程式庫在 1.0 版中通常還不完整。</span><span class="sxs-lookup"><span data-stu-id="d84f0-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="d84f0-105">良好的程式庫會隨著時間而演進、新增功能、修正錯誤，以及提升效能。</span><span class="sxs-lookup"><span data-stu-id="d84f0-105">Good libraries evolve over time, adding features, fixing bugs, and improving performance.</span></span> <span data-ttu-id="d84f0-106">您必須發行新版的 .NET 程式庫，為每個版本提供額外的價值，而不會中斷現有的使用者。</span><span class="sxs-lookup"><span data-stu-id="d84f0-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="d84f0-107">重大變更</span><span class="sxs-lookup"><span data-stu-id="d84f0-107">Breaking changes</span></span>

<span data-ttu-id="d84f0-108">如需處理版本之間中斷性變更的相關資訊，請參閱[中斷性變更](./breaking-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="d84f0-109">版本號碼</span><span class="sxs-lookup"><span data-stu-id="d84f0-109">Version numbers</span></span>

<span data-ttu-id="d84f0-110">.NET 程式庫有許多方式可以指定版本。</span><span class="sxs-lookup"><span data-stu-id="d84f0-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="d84f0-111">這些版本是最重要的：</span><span class="sxs-lookup"><span data-stu-id="d84f0-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="d84f0-112">NuGet 套件版本</span><span class="sxs-lookup"><span data-stu-id="d84f0-112">NuGet package version</span></span>

<span data-ttu-id="d84f0-113">[NuGet 套件版本](/nuget/reference/package-versioning)會顯示在 NuGet.org (Visual Studio NuGet 套件管理員) 上，並在使用套件時加入至原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="d84f0-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="d84f0-114">NuGet 套件版本是使用者通常會看到的版本號碼，當他們討論他們所使用的程式庫版本時，他們會提及它。</span><span class="sxs-lookup"><span data-stu-id="d84f0-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="d84f0-115">NuGet 會使用 NuGet 套件版本，且對執行階段行為沒有影響。</span><span class="sxs-lookup"><span data-stu-id="d84f0-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="d84f0-116">NuGet 套件識別碼與 NuGet 套件版本結合，可用來識別 NuGet 中的套件。</span><span class="sxs-lookup"><span data-stu-id="d84f0-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="d84f0-117">例如：`Newtonsoft.Json` + `11.0.2`。</span><span class="sxs-lookup"><span data-stu-id="d84f0-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="d84f0-118">帶有後置詞的套件是發行前版本套件，且具有特殊的行為，很適合用於測試。</span><span class="sxs-lookup"><span data-stu-id="d84f0-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="d84f0-119">如需詳細資訊，請參閱[發行前版本套件](./nuget.md#pre-release-packages)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="d84f0-120">因為 NuGet 套件版本是開發人員最明顯的版本，所以使用[語意版本控制 (SemVer)](https://semver.org/) 更新它是個不錯的主意。</span><span class="sxs-lookup"><span data-stu-id="d84f0-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="d84f0-121">SemVer 指出版本之間變更的重要性，並可協助開發人員在選擇要使用哪一個版本時，做出明智的決定。</span><span class="sxs-lookup"><span data-stu-id="d84f0-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="d84f0-122">例如，從 `1.0` 到 `2.0` 表示可能有潛在的中斷性變更。</span><span class="sxs-lookup"><span data-stu-id="d84f0-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="d84f0-123">✔️ 考慮使用 [SemVer 2.0.0](https://semver.org/) 來設定 NuGet 套件的版本。</span><span class="sxs-lookup"><span data-stu-id="d84f0-123">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="d84f0-124">✔️ 請務必在公用文件中使用 NuGet 套件版本，因為它是使用者通常會看到的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d84f0-124">✔️ DO use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="d84f0-125">✔️ 請務必包含發行前版本尾碼 (當發行非穩定套件時)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-125">✔️ DO include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="d84f0-126">使用者必須選擇取得發行前版本套件，以便他們了解套件不完整。</span><span class="sxs-lookup"><span data-stu-id="d84f0-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="d84f0-127">組件版本</span><span class="sxs-lookup"><span data-stu-id="d84f0-127">Assembly version</span></span>

<span data-ttu-id="d84f0-128">元件版本是 CLR 在執行時間用來選取要載入的元件版本。</span><span class="sxs-lookup"><span data-stu-id="d84f0-128">The assembly version is what the CLR uses at run time to select which version of an assembly to load.</span></span> <span data-ttu-id="d84f0-129">使用版本設定選取組件僅適用於具有強式名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="d84f0-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="d84f0-130">.NET Framework CLR 會要求完全相符，以載入強式名稱的元件。</span><span class="sxs-lookup"><span data-stu-id="d84f0-130">The .NET Framework CLR demands an exact match to load a strong-named assembly.</span></span> <span data-ttu-id="d84f0-131">例如，`Libary1, Version=1.0.0.0` 編譯時參考了 `Newtonsoft.Json, Version=11.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="d84f0-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="d84f0-132">.NET Framework 只會載入確切的版本 `11.0.0.0` 。</span><span class="sxs-lookup"><span data-stu-id="d84f0-132">.NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="d84f0-133">若要在執行時間載入不同的版本，必須將系結重新導向新增至 .NET 應用程式的設定檔。</span><span class="sxs-lookup"><span data-stu-id="d84f0-133">To load a different version at run time, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="d84f0-134">強式命名與組件版本相結合，可啟用[嚴格的組件版本載入](../assembly/versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="d84f0-135">雖然強式命名程式庫有許多優點，但通常會導致找不到元件的執行時間例外狀況，而且必須在或中修正系結重新 [導向](../../framework/configure-apps/redirect-assembly-versions.md) `app.config` `web.config` 。</span><span class="sxs-lookup"><span data-stu-id="d84f0-135">While strong naming a library has a number of benefits, it often results in run-time exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config` or `web.config` to be fixed.</span></span> <span data-ttu-id="d84f0-136">在 .NET Core 中，元件載入更寬鬆。</span><span class="sxs-lookup"><span data-stu-id="d84f0-136">In .NET Core, assembly loading is more relaxed.</span></span> <span data-ttu-id="d84f0-137">.NET Core 執行時間會在執行時間自動載入具有較高版本的元件。</span><span class="sxs-lookup"><span data-stu-id="d84f0-137">The .NET Core runtime automatically loads assemblies with a higher version at run time.</span></span>

<span data-ttu-id="d84f0-138">✔️ 考慮只在 AssemblyVersion 中包括主要版本。</span><span class="sxs-lookup"><span data-stu-id="d84f0-138">✔️ CONSIDER only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="d84f0-139">例如，Library 1.0 與 Library 1.0.1 的 AssemblyVersion 都為 `1.0.0.0`，而 Library 2.0 的 AssemblyVersion 為 `2.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="d84f0-139">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="d84f0-140">當組件版本變更頻率較低時，它可減少繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="d84f0-140">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="d84f0-141">✔️ 考慮將 AssemblyVersion 與 NuGet 套件版本的主要版本號碼保持同步。</span><span class="sxs-lookup"><span data-stu-id="d84f0-141">✔️ CONSIDER keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="d84f0-142">AssemblyVersion 包含在向使用者顯示的一些參考用訊息中，例如，例外狀況訊息中的組件名稱與組件限定類型名稱。</span><span class="sxs-lookup"><span data-stu-id="d84f0-142">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="d84f0-143">維護版本之間的關聯性，可為開發人員提供有關他們使用之版本的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d84f0-143">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="d84f0-144">❌請勿使用固定的 AssemblyVersion。</span><span class="sxs-lookup"><span data-stu-id="d84f0-144">❌ DO NOT have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="d84f0-145">雖然不會變更的 AssemblyVersion 避免了繫結重新導向的需要，但這表示只能在全域組件快取 (GAC) 中安裝單一版本的組件。</span><span class="sxs-lookup"><span data-stu-id="d84f0-145">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="d84f0-146">此外，如果另一個應用程式使用中斷性變更更新 GAC 組件，則參考 GAC 中組件的應用程式將中斷。</span><span class="sxs-lookup"><span data-stu-id="d84f0-146">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="d84f0-147">組件檔版本</span><span class="sxs-lookup"><span data-stu-id="d84f0-147">Assembly file version</span></span>

<span data-ttu-id="d84f0-148">元件檔案版本是用來顯示 Windows 中的檔案版本，不會影響執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="d84f0-148">The assembly file version is used to display a file version in Windows and has no effect on run-time behavior.</span></span> <span data-ttu-id="d84f0-149">是否設定此版本是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d84f0-149">Setting this version is optional.</span></span> <span data-ttu-id="d84f0-150">它會顯示在 Windows 檔案總管的 [檔案內容] 對話方塊中：</span><span class="sxs-lookup"><span data-stu-id="d84f0-150">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="d84f0-151">![Windows 檔案總管](./media/versioning/win-properties.png "Windows 檔案總管")</span><span class="sxs-lookup"><span data-stu-id="d84f0-151">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="d84f0-152">✔️ 考慮包括持續整合組建編號作為 AssemblyFileVersion 修訂。</span><span class="sxs-lookup"><span data-stu-id="d84f0-152">✔️ CONSIDER including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="d84f0-153">例如，您正在建置版本 1.0.0 的專案，且持續整合組建編號是 99，因此您的 AssemblyFileVersion 是 1.0.0.99。</span><span class="sxs-lookup"><span data-stu-id="d84f0-153">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="d84f0-154">✔️ 針對檔案版本，請使用 `Major.Minor.Build.Revision` 格式。</span><span class="sxs-lookup"><span data-stu-id="d84f0-154">✔️ DO use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="d84f0-155">雖然 .NET 永遠不會使用檔案版本，但 [Windows 預期檔案版本](/windows/desktop/menurc/versioninfo-resource)的格式為 `Major.Minor.Build.Revision`。</span><span class="sxs-lookup"><span data-stu-id="d84f0-155">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="d84f0-156">如果版本未遵循此格式，則會引發警告。</span><span class="sxs-lookup"><span data-stu-id="d84f0-156">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="d84f0-157">組件資訊版本</span><span class="sxs-lookup"><span data-stu-id="d84f0-157">Assembly informational version</span></span>

<span data-ttu-id="d84f0-158">組件資訊版本用於記錄其他版本資訊，對執行階段行為沒有影響。</span><span class="sxs-lookup"><span data-stu-id="d84f0-158">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="d84f0-159">是否設定此版本是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d84f0-159">Setting this version is optional.</span></span> <span data-ttu-id="d84f0-160">如果您正在使用來源連結，則此版本將在組建時使用 NuGet 套件版本加上原始檔控制版本進行設定。</span><span class="sxs-lookup"><span data-stu-id="d84f0-160">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="d84f0-161">例如，`1.0.0-beta1+204ff0a` 包括組件建置來源之原程式始碼的認可雜湊。</span><span class="sxs-lookup"><span data-stu-id="d84f0-161">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="d84f0-162">如需詳細資訊，請參閱[來源連結](./sourcelink.md)。</span><span class="sxs-lookup"><span data-stu-id="d84f0-162">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<InformationalVersion>The quick brown fox jumped over the lazy dog.</InformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="d84f0-163">如果此版本未遵循 `Major.Minor.Build.Revision` 格式，則舊版的 Visual Studio 會引發建置警告。</span><span class="sxs-lookup"><span data-stu-id="d84f0-163">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="d84f0-164">您可以安心略過該警告。</span><span class="sxs-lookup"><span data-stu-id="d84f0-164">The warning can be safely ignored.</span></span>

<span data-ttu-id="d84f0-165">❌避免設定您自己的組件資訊版本。</span><span class="sxs-lookup"><span data-stu-id="d84f0-165">❌ AVOID setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="d84f0-166">允許 SourceLink 自動產生包含 NuGet 與原始檔控制中繼資料的版本。</span><span class="sxs-lookup"><span data-stu-id="d84f0-166">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d84f0-167">[上一個](publish-nuget-package.md) 
>[下一步](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="d84f0-167">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
