---
title: 適用于 .NET 的 MSBuild 屬性
description: .NET Core SDK 所瞭解之 MSBuild 屬性的參考。
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 105b7d67ea24515ea88481cb4a4fe42d2a03cfd0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506781"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="9944d-103">.NET Core SDK 專案的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="9944d-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="9944d-104">此頁面描述用於設定 .NET Core 專案的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="9944d-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="9944d-105">此頁面為進行中的工作，且不會列出 .NET Core SDK 的所有有用 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="9944d-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="9944d-106">如需一般 MSBuild 屬性的清單，請參閱[一般 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="9944d-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="9944d-107">架構屬性</span><span class="sxs-lookup"><span data-stu-id="9944d-107">Framework properties</span></span>

- [<span data-ttu-id="9944d-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="9944d-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="9944d-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="9944d-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="9944d-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="9944d-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="9944d-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="9944d-111">TargetFramework</span></span>

<span data-ttu-id="9944d-112">`TargetFramework`屬性會指定應用程式的目標 framework 版本，它會隱含地參考[中繼套件](../packages.md#metapackages)。</span><span class="sxs-lookup"><span data-stu-id="9944d-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="9944d-113">如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="9944d-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="9944d-114">如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9944d-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="9944d-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="9944d-115">TargetFrameworks</span></span>

<span data-ttu-id="9944d-116">當您`TargetFrameworks`想要讓應用程式以多個平臺為目標時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="9944d-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="9944d-117">如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="9944d-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="9944d-118">如果`TargetFramework`指定了（單數），則會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="9944d-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="9944d-119">如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="9944d-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="9944d-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="9944d-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="9944d-121">這個屬性僅適用于使用`netstandard1.x`的專案。</span><span class="sxs-lookup"><span data-stu-id="9944d-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="9944d-122">它不適用於使用`netstandard2.x`的專案。</span><span class="sxs-lookup"><span data-stu-id="9944d-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="9944d-123">當您`NetStandardImplicitPackageVersion`想要指定的 framework 版本低於[中繼套件](../packages.md#metapackages)版本時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="9944d-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="9944d-124">下列範例中的專案檔會以`netstandard1.3`為目標，但會使用`NETStandard.Library`的1.6.0 版本。</span><span class="sxs-lookup"><span data-stu-id="9944d-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="9944d-125">發佈屬性</span><span class="sxs-lookup"><span data-stu-id="9944d-125">Publish properties</span></span>

- [<span data-ttu-id="9944d-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="9944d-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="9944d-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="9944d-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="9944d-128">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="9944d-128">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="9944d-129">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="9944d-129">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="9944d-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="9944d-130">RuntimeIdentifier</span></span>

<span data-ttu-id="9944d-131">屬性可讓您指定專案的單一[執行時間識別碼（RID）。](../rid-catalog.md) `RuntimeIdentifier`</span><span class="sxs-lookup"><span data-stu-id="9944d-131">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9944d-132">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="9944d-132">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="9944d-133">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="9944d-133">RuntimeIdentifiers</span></span>

<span data-ttu-id="9944d-134">屬性可讓您指定專案的[執行時間識別碼（rid）清單（](../rid-catalog.md)以分號分隔）。 `RuntimeIdentifiers`</span><span class="sxs-lookup"><span data-stu-id="9944d-134">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9944d-135">如果您需要針對多個執行時間發行，請使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="9944d-135">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="9944d-136">`RuntimeIdentifiers`會在還原時使用，以確保正確的資產在圖形中。</span><span class="sxs-lookup"><span data-stu-id="9944d-136">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="9944d-137">`RuntimeIdentifier`（單數）可以在只需要單一執行時間時提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="9944d-137">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="9944d-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="9944d-138">TrimmerRootAssembly</span></span>

<span data-ttu-id="9944d-139">`TrimmerRootAssembly`專案可讓您將元件從[*修剪*](../deploying/trim-self-contained.md)中排除。</span><span class="sxs-lookup"><span data-stu-id="9944d-139">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="9944d-140">修剪是從封裝的應用程式中移除執行時間未使用元件的程式。</span><span class="sxs-lookup"><span data-stu-id="9944d-140">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="9944d-141">在某些情況下，修剪可能會不正確地移除所需的參考。</span><span class="sxs-lookup"><span data-stu-id="9944d-141">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="9944d-142">下列 XML 會將`System.Security`元件從修剪中排除。</span><span class="sxs-lookup"><span data-stu-id="9944d-142">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="9944d-143">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="9944d-143">UseAppHost</span></span>

<span data-ttu-id="9944d-144">`UseAppHost`屬性是在 .NET Core SDK 的2.1.400 版本中引進。</span><span class="sxs-lookup"><span data-stu-id="9944d-144">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="9944d-145">它會控制是否針對部署建立原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="9944d-145">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="9944d-146">獨立部署需要原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="9944d-146">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="9944d-147">在 .NET Core 3.0 和更新版本中，預設會建立與 framework 相依的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="9944d-147">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="9944d-148">將`UseAppHost`屬性設定為`false` ，以停用可執行檔的產生。</span><span class="sxs-lookup"><span data-stu-id="9944d-148">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="9944d-149">如需部署的詳細資訊，請參閱[.Net Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9944d-149">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="9944d-150">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="9944d-150">Compile properties</span></span>

- [<span data-ttu-id="9944d-151">LangVersion</span><span class="sxs-lookup"><span data-stu-id="9944d-151">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="9944d-152">LangVersion</span><span class="sxs-lookup"><span data-stu-id="9944d-152">LangVersion</span></span>

<span data-ttu-id="9944d-153">`LangVersion`屬性可讓您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="9944d-153">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="9944d-154">例如，如果您想要存取 c # preview 功能，請`LangVersion`將`preview`設定為。</span><span class="sxs-lookup"><span data-stu-id="9944d-154">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="9944d-155">如需詳細資訊，請參閱[c # 語言版本](../../csharp/language-reference/configure-language-version.md#override-a-default)設定。</span><span class="sxs-lookup"><span data-stu-id="9944d-155">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="9944d-156">執行時間設定屬性</span><span class="sxs-lookup"><span data-stu-id="9944d-156">Run-time configuration properties</span></span>

<span data-ttu-id="9944d-157">您可以在應用程式的專案檔中指定 MSBuild 屬性，以設定一些執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="9944d-157">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="9944d-158">如需其他設定執行時間行為方式的相關資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="9944d-158">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="9944d-159">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9944d-159">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="9944d-160">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="9944d-160">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="9944d-161">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9944d-161">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="9944d-162">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9944d-162">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="9944d-163">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9944d-163">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="9944d-164">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="9944d-164">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="9944d-165">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="9944d-165">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="9944d-166">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="9944d-166">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="9944d-167">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="9944d-167">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="9944d-168">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9944d-168">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="9944d-169">`ConcurrentGarbageCollection`屬性會設定是否啟用[背景（並行）垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="9944d-169">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="9944d-170">將值設定為`false` ，以停用背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="9944d-170">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="9944d-171">如需詳細資訊，請參閱 system.string [. [並行/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)]。</span><span class="sxs-lookup"><span data-stu-id="9944d-171">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a><span data-ttu-id="9944d-172">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="9944d-172">InvariantGlobalization</span></span>

<span data-ttu-id="9944d-173">屬性會設定應用程式是否以*全球化不變*模式執行，這表示它無法存取特定文化特性的資料。 `InvariantGlobalization`</span><span class="sxs-lookup"><span data-stu-id="9944d-173">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="9944d-174">將值設定為`true` ，以在全球化-不變模式下執行。</span><span class="sxs-lookup"><span data-stu-id="9944d-174">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="9944d-175">如需詳細資訊，請參閱不[變模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="9944d-175">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="9944d-176">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9944d-176">RetainVMGarbageCollection</span></span>

<span data-ttu-id="9944d-177">`RetainVMGarbageCollection`屬性會將垃圾收集行程設定為將已刪除的記憶體區段放在待命清單上以供日後使用或釋放它們。</span><span class="sxs-lookup"><span data-stu-id="9944d-177">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="9944d-178">將值設定為`true` ，會指示垃圾收集行程將區段放在待命清單上。</span><span class="sxs-lookup"><span data-stu-id="9944d-178">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="9944d-179">如需詳細資訊，請參閱[RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm)。</span><span class="sxs-lookup"><span data-stu-id="9944d-179">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="9944d-180">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="9944d-180">ServerGarbageCollection</span></span>

<span data-ttu-id="9944d-181">`ServerGarbageCollection`屬性會設定應用程式是否使用[工作站垃圾收集或伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="9944d-181">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="9944d-182">將值設定為`true` ，以使用伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="9944d-182">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="9944d-183">如需詳細資訊，請參閱[system.object/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)。</span><span class="sxs-lookup"><span data-stu-id="9944d-183">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="9944d-184">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="9944d-184">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="9944d-185">`ThreadPoolMaxThreads`屬性會設定背景工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="9944d-185">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="9944d-186">如需詳細資訊，請參閱[執行緒上限](../run-time-config/threading.md#maximum-threads)。</span><span class="sxs-lookup"><span data-stu-id="9944d-186">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="9944d-187">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="9944d-187">ThreadPoolMinThreads</span></span>

<span data-ttu-id="9944d-188">`ThreadPoolMinThreads`屬性會設定背景工作執行緒集區的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="9944d-188">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="9944d-189">如需詳細資訊，請參閱[最小線程](../run-time-config/threading.md#minimum-threads)。</span><span class="sxs-lookup"><span data-stu-id="9944d-189">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a><span data-ttu-id="9944d-190">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="9944d-190">TieredCompilation</span></span>

<span data-ttu-id="9944d-191">屬性會設定即時（JIT）編譯器是否使用[分層式編譯。](../whats-new/dotnet-core-3-0.md#tiered-compilation) `TieredCompilation`</span><span class="sxs-lookup"><span data-stu-id="9944d-191">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="9944d-192">將值設定為`false` ，以停用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="9944d-192">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="9944d-193">如需詳細資訊，請參閱[分層式編譯](../run-time-config/compilation.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="9944d-193">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="9944d-194">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="9944d-194">TieredCompilationQuickJit</span></span>

<span data-ttu-id="9944d-195">`TieredCompilationQuickJit`屬性會設定 JIT 編譯程式是否使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="9944d-195">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="9944d-196">將值設為`false`以停用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="9944d-196">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="9944d-197">如需詳細資訊，請參閱[快速 JIT](../run-time-config/compilation.md#quick-jit)。</span><span class="sxs-lookup"><span data-stu-id="9944d-197">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="9944d-198">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="9944d-198">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="9944d-199">`TieredCompilationQuickJitForLoops`屬性會設定 JIT 編譯程式是否針對包含迴圈的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="9944d-199">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="9944d-200">將值設定為`true` ，以啟用包含迴圈之方法的快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="9944d-200">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="9944d-201">如需詳細資訊，請參閱[快速 JIT for 迴圈](../run-time-config/compilation.md#quick-jit-for-loops)。</span><span class="sxs-lookup"><span data-stu-id="9944d-201">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a><span data-ttu-id="9944d-202">NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="9944d-202">NuGet packages</span></span>

- [<span data-ttu-id="9944d-203">PackageReference</span><span class="sxs-lookup"><span data-stu-id="9944d-203">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="9944d-204">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="9944d-204">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="9944d-205">PackageReference</span><span class="sxs-lookup"><span data-stu-id="9944d-205">PackageReference</span></span>

<span data-ttu-id="9944d-206">此`PackageReference`專案可讓您指定 NuGet 相依性。</span><span class="sxs-lookup"><span data-stu-id="9944d-206">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="9944d-207">例如，您可能想要參考單一封裝，而不是[中繼套件](../packages.md#metapackages)。</span><span class="sxs-lookup"><span data-stu-id="9944d-207">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="9944d-208">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="9944d-208">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="9944d-209">下列範例中的專案檔程式碼片段會參考[system.webserver](https://www.nuget.org/packages/System.Runtime/)封裝。</span><span class="sxs-lookup"><span data-stu-id="9944d-209">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="9944d-210">如需詳細資訊，請參閱[專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="9944d-210">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="9944d-211">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="9944d-211">AssetTargetFallback</span></span>

<span data-ttu-id="9944d-212">`AssetTargetFallback`屬性可讓您為專案所參考的專案和專案所使用的 NuGet 套件，指定其他相容的架構版本。</span><span class="sxs-lookup"><span data-stu-id="9944d-212">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="9944d-213">例如，如果您使用`PackageReference`指定封裝相依性，但該套件並未包含與您專案的`TargetFramework`相容的資產，則該`AssetTargetFallback`屬性會開始播放。</span><span class="sxs-lookup"><span data-stu-id="9944d-213">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="9944d-214">所參考封裝的相容性是使用中`AssetTargetFallback`指定的每個目標架構來間隔。</span><span class="sxs-lookup"><span data-stu-id="9944d-214">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="9944d-215">您可以將`AssetTargetFallback`屬性設定為一個或多個[目標 framework 版本](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="9944d-215">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="9944d-216">套件和還原目標</span><span class="sxs-lookup"><span data-stu-id="9944d-216">Pack and restore targets</span></span>

<span data-ttu-id="9944d-217">MSBuild 15.1 引進`pack`和`restore`還原 NuGet 套件的目標，做為組建的一部分。</span><span class="sxs-lookup"><span data-stu-id="9944d-217">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="9944d-218">如需這些目標之 MSBuild 屬性的相關資訊， `PackageTargetFallback`包括，請參閱[NuGet 套件和還原為 MSBuild 目標](/nuget/reference/msbuild-targets)。</span><span class="sxs-lookup"><span data-stu-id="9944d-218">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="9944d-219">請參閱</span><span class="sxs-lookup"><span data-stu-id="9944d-219">See also</span></span>

- [<span data-ttu-id="9944d-220">MSBuild 架構參考</span><span class="sxs-lookup"><span data-stu-id="9944d-220">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="9944d-221">一般 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="9944d-221">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="9944d-222">NuGet 套件的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="9944d-222">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="9944d-223">NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="9944d-223">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="9944d-224">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="9944d-224">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
