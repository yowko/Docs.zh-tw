---
title: 適用于 .NET 的 MSBuild 屬性
description: .NET Core SDK 所瞭解之 MSBuild 屬性的參考。
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 800ff59310d8437d7f770bf20a5bdf37714f8515
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795569"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="325f0-103">.NET Core SDK 專案的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="325f0-104">此頁面描述用於設定 .NET Core 專案的 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="325f0-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span> <span data-ttu-id="325f0-105">您可以將每個屬性的*中繼資料*指定為屬性的子項目。</span><span class="sxs-lookup"><span data-stu-id="325f0-105">You can specify *metadata* for each property as child elements of the property.</span></span>

> [!NOTE]
> <span data-ttu-id="325f0-106">此頁面為進行中的工作，且不會列出 .NET Core SDK 的所有有用 MSBuild 屬性。</span><span class="sxs-lookup"><span data-stu-id="325f0-106">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="325f0-107">如需一般 MSBuild 屬性的清單，請參閱[一般 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。</span><span class="sxs-lookup"><span data-stu-id="325f0-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="325f0-108">架構屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-108">Framework properties</span></span>

- [<span data-ttu-id="325f0-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="325f0-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="325f0-110">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="325f0-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="325f0-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="325f0-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="325f0-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="325f0-112">TargetFramework</span></span>

<span data-ttu-id="325f0-113">`TargetFramework`屬性會指定應用程式的目標 framework 版本，它會隱含地參考[中繼套件](../packages.md#metapackages)。</span><span class="sxs-lookup"><span data-stu-id="325f0-113">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="325f0-114">如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="325f0-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="325f0-115">如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="325f0-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="325f0-116">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="325f0-116">TargetFrameworks</span></span>

<span data-ttu-id="325f0-117">當您`TargetFrameworks`想要讓應用程式以多個平臺為目標時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="325f0-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="325f0-118">如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="325f0-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="325f0-119">如果`TargetFramework`指定了（單數），則會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="325f0-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="325f0-120">如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。</span><span class="sxs-lookup"><span data-stu-id="325f0-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="325f0-121">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="325f0-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="325f0-122">這個屬性僅適用于使用`netstandard1.x`的專案。</span><span class="sxs-lookup"><span data-stu-id="325f0-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="325f0-123">它不適用於使用`netstandard2.x`的專案。</span><span class="sxs-lookup"><span data-stu-id="325f0-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="325f0-124">當您`NetStandardImplicitPackageVersion`想要指定的 framework 版本低於[中繼套件](../packages.md#metapackages)版本時，請使用屬性。</span><span class="sxs-lookup"><span data-stu-id="325f0-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="325f0-125">下列範例中的專案檔會以`netstandard1.3`為目標，但會使用`NETStandard.Library`的1.6.0 版本。</span><span class="sxs-lookup"><span data-stu-id="325f0-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="325f0-126">封裝屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-126">Package properties</span></span>

<span data-ttu-id="325f0-127">您可以指定`PackageId`、 `PackageVersion`、 `PackageIcon`、 `Title`和`Description`等屬性，以描述從專案建立的封裝。</span><span class="sxs-lookup"><span data-stu-id="325f0-127">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="325f0-128">如需這些和其他屬性的詳細資訊，請參閱[pack target](/nuget/reference/msbuild-targets#pack-target)。</span><span class="sxs-lookup"><span data-stu-id="325f0-128">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties"></a><span data-ttu-id="325f0-129">發佈屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-129">Publish properties</span></span>

- [<span data-ttu-id="325f0-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="325f0-130">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="325f0-131">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="325f0-131">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="325f0-132">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="325f0-132">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="325f0-133">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="325f0-133">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="325f0-134">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="325f0-134">RuntimeIdentifier</span></span>

<span data-ttu-id="325f0-135">屬性可讓您指定專案的單一[執行時間識別碼（RID）。](../rid-catalog.md) `RuntimeIdentifier`</span><span class="sxs-lookup"><span data-stu-id="325f0-135">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="325f0-136">RID 允許發佈獨立式部署。</span><span class="sxs-lookup"><span data-stu-id="325f0-136">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="325f0-137">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="325f0-137">RuntimeIdentifiers</span></span>

<span data-ttu-id="325f0-138">屬性可讓您指定專案的[執行時間識別碼（rid）清單（](../rid-catalog.md)以分號分隔）。 `RuntimeIdentifiers`</span><span class="sxs-lookup"><span data-stu-id="325f0-138">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="325f0-139">如果您需要針對多個執行時間發行，請使用這個屬性。</span><span class="sxs-lookup"><span data-stu-id="325f0-139">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="325f0-140">`RuntimeIdentifiers`會在還原時使用，以確保正確的資產在圖形中。</span><span class="sxs-lookup"><span data-stu-id="325f0-140">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="325f0-141">`RuntimeIdentifier`（單數）可以在只需要單一執行時間時提供更快速的組建。</span><span class="sxs-lookup"><span data-stu-id="325f0-141">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="325f0-142">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="325f0-142">TrimmerRootAssembly</span></span>

<span data-ttu-id="325f0-143">`TrimmerRootAssembly`專案可讓您將元件從[*修剪*](../deploying/trim-self-contained.md)中排除。</span><span class="sxs-lookup"><span data-stu-id="325f0-143">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="325f0-144">修剪是從封裝的應用程式中移除執行時間未使用元件的程式。</span><span class="sxs-lookup"><span data-stu-id="325f0-144">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="325f0-145">在某些情況下，修剪可能會不正確地移除所需的參考。</span><span class="sxs-lookup"><span data-stu-id="325f0-145">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="325f0-146">下列 XML 會將`System.Security`元件從修剪中排除。</span><span class="sxs-lookup"><span data-stu-id="325f0-146">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="325f0-147">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="325f0-147">UseAppHost</span></span>

<span data-ttu-id="325f0-148">`UseAppHost`屬性是在 .NET Core SDK 的2.1.400 版本中引進。</span><span class="sxs-lookup"><span data-stu-id="325f0-148">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="325f0-149">它會控制是否針對部署建立原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="325f0-149">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="325f0-150">獨立部署需要原生可執行檔。</span><span class="sxs-lookup"><span data-stu-id="325f0-150">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="325f0-151">在 .NET Core 3.0 和更新版本中，預設會建立與 framework 相依的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="325f0-151">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="325f0-152">將`UseAppHost`屬性設定為`false` ，以停用可執行檔的產生。</span><span class="sxs-lookup"><span data-stu-id="325f0-152">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="325f0-153">如需部署的詳細資訊，請參閱[.Net Core 應用程式部署](../deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="325f0-153">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="325f0-154">編譯屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-154">Compile properties</span></span>

- [<span data-ttu-id="325f0-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="325f0-155">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="325f0-156">LangVersion</span><span class="sxs-lookup"><span data-stu-id="325f0-156">LangVersion</span></span>

<span data-ttu-id="325f0-157">`LangVersion`屬性可讓您指定特定的程式設計語言版本。</span><span class="sxs-lookup"><span data-stu-id="325f0-157">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="325f0-158">例如，如果您想要存取 c # preview 功能，請`LangVersion`將`preview`設定為。</span><span class="sxs-lookup"><span data-stu-id="325f0-158">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="325f0-159">如需詳細資訊，請參閱[c # 語言版本](../../csharp/language-reference/configure-language-version.md#override-a-default)設定。</span><span class="sxs-lookup"><span data-stu-id="325f0-159">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="325f0-160">執行時間設定屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-160">Run-time configuration properties</span></span>

<span data-ttu-id="325f0-161">您可以在應用程式的專案檔中指定 MSBuild 屬性，以設定一些執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="325f0-161">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="325f0-162">如需其他設定執行時間行為方式的相關資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md)。</span><span class="sxs-lookup"><span data-stu-id="325f0-162">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="325f0-163">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="325f0-163">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="325f0-164">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="325f0-164">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="325f0-165">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="325f0-165">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="325f0-166">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="325f0-166">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="325f0-167">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="325f0-167">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="325f0-168">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="325f0-168">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="325f0-169">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="325f0-169">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="325f0-170">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="325f0-170">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="325f0-171">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="325f0-171">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="325f0-172">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="325f0-172">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="325f0-173">`ConcurrentGarbageCollection`屬性會設定是否啟用[背景（並行）垃圾收集](../../standard/garbage-collection/background-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="325f0-173">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="325f0-174">將值設定為`false` ，以停用背景垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="325f0-174">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="325f0-175">如需詳細資訊，請參閱 system.string [. [並行/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)]。</span><span class="sxs-lookup"><span data-stu-id="325f0-175">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="325f0-176">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="325f0-176">InvariantGlobalization</span></span>

<span data-ttu-id="325f0-177">屬性會設定應用程式是否以*全球化不變*模式執行，這表示它無法存取特定文化特性的資料。 `InvariantGlobalization`</span><span class="sxs-lookup"><span data-stu-id="325f0-177">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="325f0-178">將值設定為`true` ，以在全球化-不變模式下執行。</span><span class="sxs-lookup"><span data-stu-id="325f0-178">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="325f0-179">如需詳細資訊，請參閱不[變模式](../run-time-config/globalization.md#invariant-mode)。</span><span class="sxs-lookup"><span data-stu-id="325f0-179">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="325f0-180">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="325f0-180">RetainVMGarbageCollection</span></span>

<span data-ttu-id="325f0-181">`RetainVMGarbageCollection`屬性會將垃圾收集行程設定為將已刪除的記憶體區段放在待命清單上以供日後使用或釋放它們。</span><span class="sxs-lookup"><span data-stu-id="325f0-181">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="325f0-182">將值設定為`true` ，會指示垃圾收集行程將區段放在待命清單上。</span><span class="sxs-lookup"><span data-stu-id="325f0-182">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="325f0-183">如需詳細資訊，請參閱[RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm)。</span><span class="sxs-lookup"><span data-stu-id="325f0-183">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="325f0-184">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="325f0-184">ServerGarbageCollection</span></span>

<span data-ttu-id="325f0-185">`ServerGarbageCollection`屬性會設定應用程式是否使用[工作站垃圾收集或伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。</span><span class="sxs-lookup"><span data-stu-id="325f0-185">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="325f0-186">將值設定為`true` ，以使用伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="325f0-186">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="325f0-187">如需詳細資訊，請參閱[system.object/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)。</span><span class="sxs-lookup"><span data-stu-id="325f0-187">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="325f0-188">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="325f0-188">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="325f0-189">`ThreadPoolMaxThreads`屬性會設定背景工作執行緒集區的執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="325f0-189">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="325f0-190">如需詳細資訊，請參閱[執行緒上限](../run-time-config/threading.md#maximum-threads)。</span><span class="sxs-lookup"><span data-stu-id="325f0-190">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="325f0-191">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="325f0-191">ThreadPoolMinThreads</span></span>

<span data-ttu-id="325f0-192">`ThreadPoolMinThreads`屬性會設定背景工作執行緒集區的執行緒數目下限。</span><span class="sxs-lookup"><span data-stu-id="325f0-192">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="325f0-193">如需詳細資訊，請參閱[最小線程](../run-time-config/threading.md#minimum-threads)。</span><span class="sxs-lookup"><span data-stu-id="325f0-193">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="325f0-194">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="325f0-194">TieredCompilation</span></span>

<span data-ttu-id="325f0-195">屬性會設定即時（JIT）編譯器是否使用[分層式編譯。](../whats-new/dotnet-core-3-0.md#tiered-compilation) `TieredCompilation`</span><span class="sxs-lookup"><span data-stu-id="325f0-195">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="325f0-196">將值設定為`false` ，以停用階層式編譯。</span><span class="sxs-lookup"><span data-stu-id="325f0-196">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="325f0-197">如需詳細資訊，請參閱[分層式編譯](../run-time-config/compilation.md#tiered-compilation)。</span><span class="sxs-lookup"><span data-stu-id="325f0-197">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="325f0-198">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="325f0-198">TieredCompilationQuickJit</span></span>

<span data-ttu-id="325f0-199">`TieredCompilationQuickJit`屬性會設定 JIT 編譯程式是否使用快速 jit。</span><span class="sxs-lookup"><span data-stu-id="325f0-199">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="325f0-200">將值設為`false`以停用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="325f0-200">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="325f0-201">如需詳細資訊，請參閱[快速 JIT](../run-time-config/compilation.md#quick-jit)。</span><span class="sxs-lookup"><span data-stu-id="325f0-201">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="325f0-202">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="325f0-202">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="325f0-203">`TieredCompilationQuickJitForLoops`屬性會設定 JIT 編譯程式是否針對包含迴圈的方法使用快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="325f0-203">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="325f0-204">將值設定為`true` ，以啟用包含迴圈之方法的快速 JIT。</span><span class="sxs-lookup"><span data-stu-id="325f0-204">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="325f0-205">如需詳細資訊，請參閱[快速 JIT for 迴圈](../run-time-config/compilation.md#quick-jit-for-loops)。</span><span class="sxs-lookup"><span data-stu-id="325f0-205">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="325f0-206">參考屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-206">Reference properties</span></span>

- [<span data-ttu-id="325f0-207">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="325f0-207">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="325f0-208">PackageReference</span><span class="sxs-lookup"><span data-stu-id="325f0-208">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="325f0-209">專案參考</span><span class="sxs-lookup"><span data-stu-id="325f0-209">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="325f0-210">參考</span><span class="sxs-lookup"><span data-stu-id="325f0-210">Reference</span></span>](#reference)
- [<span data-ttu-id="325f0-211">還原屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-211">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="325f0-212">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="325f0-212">AssetTargetFallback</span></span>

<span data-ttu-id="325f0-213">`AssetTargetFallback`屬性可讓您為專案參考和 NuGet 套件指定其他相容的架構版本。</span><span class="sxs-lookup"><span data-stu-id="325f0-213">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="325f0-214">例如，如果您使用`PackageReference`指定封裝相依性，但該套件並未包含與您專案的`TargetFramework`相容的資產，則該`AssetTargetFallback`屬性會開始播放。</span><span class="sxs-lookup"><span data-stu-id="325f0-214">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="325f0-215">所參考封裝的相容性是使用中`AssetTargetFallback`指定的每個目標架構來間隔。</span><span class="sxs-lookup"><span data-stu-id="325f0-215">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="325f0-216">您可以將`AssetTargetFallback`屬性設定為一個或多個[目標 framework 版本](../../standard/frameworks.md#supported-target-framework-versions)。</span><span class="sxs-lookup"><span data-stu-id="325f0-216">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="325f0-217">PackageReference</span><span class="sxs-lookup"><span data-stu-id="325f0-217">PackageReference</span></span>

<span data-ttu-id="325f0-218">`PackageReference`定義 NuGet 套件的參考。</span><span class="sxs-lookup"><span data-stu-id="325f0-218">The `PackageReference` defines a reference to a NuGet package.</span></span> <span data-ttu-id="325f0-219">例如，您可能想要參考單一封裝，而不是[中繼套件](../packages.md#metapackages)。</span><span class="sxs-lookup"><span data-stu-id="325f0-219">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span>

<span data-ttu-id="325f0-220">`Include` 屬性會指定套件識別碼。</span><span class="sxs-lookup"><span data-stu-id="325f0-220">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="325f0-221">`Version`屬性會指定版本或版本範圍。</span><span class="sxs-lookup"><span data-stu-id="325f0-221">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="325f0-222">如需有關如何指定最小版本、最大版本、範圍或完全相符的詳細資訊，請參閱[版本範圍](/nuget/concepts/package-versioning#version-ranges)。</span><span class="sxs-lookup"><span data-stu-id="325f0-222">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="325f0-223">您也可以將下列中繼資料加入至專案參考： `IncludeAssets`、 `ExcludeAssets`和`PrivateAssets`。</span><span class="sxs-lookup"><span data-stu-id="325f0-223">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="325f0-224">下列範例中的專案檔程式碼片段會參考[system.webserver](https://www.nuget.org/packages/System.Runtime/)封裝。</span><span class="sxs-lookup"><span data-stu-id="325f0-224">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="325f0-225">如需詳細資訊，請參閱[專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。</span><span class="sxs-lookup"><span data-stu-id="325f0-225">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="325f0-226">專案參考</span><span class="sxs-lookup"><span data-stu-id="325f0-226">ProjectReference</span></span>

<span data-ttu-id="325f0-227">`ProjectReference`專案會定義對另一個專案的參考。</span><span class="sxs-lookup"><span data-stu-id="325f0-227">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="325f0-228">參考的專案會新增為 NuGet 套件相依性，亦即，它會被視為與相同`PackageReference`。</span><span class="sxs-lookup"><span data-stu-id="325f0-228">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="325f0-229">`Include`屬性會指定專案的路徑。</span><span class="sxs-lookup"><span data-stu-id="325f0-229">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="325f0-230">您也可以將下列中繼資料加入至專案參考： `IncludeAssets`、 `ExcludeAssets`和`PrivateAssets`。</span><span class="sxs-lookup"><span data-stu-id="325f0-230">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="325f0-231">下列範例中的專案檔程式碼片段會參考名為`Project2`的專案。</span><span class="sxs-lookup"><span data-stu-id="325f0-231">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="325f0-232">參考</span><span class="sxs-lookup"><span data-stu-id="325f0-232">Reference</span></span>

<span data-ttu-id="325f0-233">`Reference`專案會定義元件檔的參考。</span><span class="sxs-lookup"><span data-stu-id="325f0-233">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="325f0-234">`Include`屬性會指定檔案名，而`HintPath`子項目會指定元件的路徑。</span><span class="sxs-lookup"><span data-stu-id="325f0-234">The `Include` attribute specifies the name of the file, and the `HintPath` child element specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="325f0-235">還原屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-235">Restore properties</span></span>

<span data-ttu-id="325f0-236">還原參考的套件會安裝其所有的直接相依性，以及這些相依性的所有相依性。</span><span class="sxs-lookup"><span data-stu-id="325f0-236">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="325f0-237">您可以藉由指定如`RestorePackagesPath`和`RestoreIgnoreFailedSources`的屬性來自訂封裝還原。</span><span class="sxs-lookup"><span data-stu-id="325f0-237">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="325f0-238">如需這些和其他屬性的詳細資訊，請參閱[還原目標](/nuget/reference/msbuild-targets#restore-target)。</span><span class="sxs-lookup"><span data-stu-id="325f0-238">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="325f0-239">請參閱</span><span class="sxs-lookup"><span data-stu-id="325f0-239">See also</span></span>

- [<span data-ttu-id="325f0-240">MSBuild 架構參考</span><span class="sxs-lookup"><span data-stu-id="325f0-240">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="325f0-241">一般 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-241">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="325f0-242">NuGet 套件的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-242">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="325f0-243">NuGet 還原的 MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="325f0-243">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="325f0-244">自訂群組建</span><span class="sxs-lookup"><span data-stu-id="325f0-244">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
