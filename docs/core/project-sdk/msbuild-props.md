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
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>.NET Core SDK 專案的 MSBuild 屬性

此頁面描述用於設定 .NET Core 專案的 MSBuild 屬性。

> [!NOTE]
> 此頁面為進行中的工作，且不會列出 .NET Core SDK 的所有有用 MSBuild 屬性。 如需一般 MSBuild 屬性的清單，請參閱[一般 msbuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)。

## <a name="framework-properties"></a>架構屬性

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework`屬性會指定應用程式的目標 framework 版本，它會隱含地參考[中繼套件](../packages.md#metapackages)。 如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。

### <a name="targetframeworks"></a>TargetFrameworks

當您`TargetFrameworks`想要讓應用程式以多個平臺為目標時，請使用屬性。 如需有效的目標 framework 名字標記清單，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md#supported-target-framework-versions)。

> [!NOTE]
> 如果`TargetFramework`指定了（單數），則會忽略這個屬性。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

如需詳細資訊，請參閱[SDK 樣式專案中的目標 framework](../../standard/frameworks.md)。

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> 這個屬性僅適用于使用`netstandard1.x`的專案。 它不適用於使用`netstandard2.x`的專案。

當您`NetStandardImplicitPackageVersion`想要指定的 framework 版本低於[中繼套件](../packages.md#metapackages)版本時，請使用屬性。 下列範例中的專案檔會以`netstandard1.3`為目標，但會使用`NETStandard.Library`的1.6.0 版本。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>發佈屬性

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

屬性可讓您指定專案的單一[執行時間識別碼（RID）。](../rid-catalog.md) `RuntimeIdentifier` RID 允許發佈獨立式部署。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

屬性可讓您指定專案的[執行時間識別碼（rid）清單（](../rid-catalog.md)以分號分隔）。 `RuntimeIdentifiers` 如果您需要針對多個執行時間發行，請使用這個屬性。 `RuntimeIdentifiers`會在還原時使用，以確保正確的資產在圖形中。

> [!TIP]
> `RuntimeIdentifier`（單數）可以在只需要單一執行時間時提供更快速的組建。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

`TrimmerRootAssembly`專案可讓您將元件從[*修剪*](../deploying/trim-self-contained.md)中排除。 修剪是從封裝的應用程式中移除執行時間未使用元件的程式。 在某些情況下，修剪可能會不正確地移除所需的參考。

下列 XML 會將`System.Security`元件從修剪中排除。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost`屬性是在 .NET Core SDK 的2.1.400 版本中引進。 它會控制是否針對部署建立原生可執行檔。 獨立部署需要原生可執行檔。

在 .NET Core 3.0 和更新版本中，預設會建立與 framework 相依的可執行檔。 將`UseAppHost`屬性設定為`false` ，以停用可執行檔的產生。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

如需部署的詳細資訊，請參閱[.Net Core 應用程式部署](../deploying/index.md)。

## <a name="compile-properties"></a>編譯屬性

- [LangVersion](#langversion)

### <a name="langversion"></a>LangVersion

`LangVersion`屬性可讓您指定特定的程式設計語言版本。 例如，如果您想要存取 c # preview 功能，請`LangVersion`將`preview`設定為。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

如需詳細資訊，請參閱[c # 語言版本](../../csharp/language-reference/configure-language-version.md#override-a-default)設定。

## <a name="run-time-configuration-properties"></a>執行時間設定屬性

您可以在應用程式的專案檔中指定 MSBuild 屬性，以設定一些執行時間行為。 如需其他設定執行時間行為方式的相關資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md)。

- [ConcurrentGarbageCollection](#concurrentgarbagecollection)
- [InvariantGlobalization](#invariantglobalization)
- [RetainVMGarbageCollection](#retainvmgarbagecollection)
- [ServerGarbageCollection](#servergarbagecollection)
- [ThreadPoolMaxThreads](#threadpoolmaxthreads)
- [ThreadPoolMinThreads](#threadpoolminthreads)
- [TieredCompilation](#tieredcompilation)
- [TieredCompilationQuickJit](#tieredcompilationquickjit)
- [TieredCompilationQuickJitForLoops](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a>ConcurrentGarbageCollection

`ConcurrentGarbageCollection`屬性會設定是否啟用[背景（並行）垃圾收集](../../standard/garbage-collection/background-gc.md)。 將值設定為`false` ，以停用背景垃圾收集。 如需詳細資訊，請參閱 system.string [. [並行/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent)]。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

屬性會設定應用程式是否以*全球化不變*模式執行，這表示它無法存取特定文化特性的資料。 `InvariantGlobalization` 將值設定為`true` ，以在全球化-不變模式下執行。 如需詳細資訊，請參閱不[變模式](../run-time-config/globalization.md#invariant-mode)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

`RetainVMGarbageCollection`屬性會將垃圾收集行程設定為將已刪除的記憶體區段放在待命清單上以供日後使用或釋放它們。 將值設定為`true` ，會指示垃圾收集行程將區段放在待命清單上。 如需詳細資訊，請參閱[RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

`ServerGarbageCollection`屬性會設定應用程式是否使用[工作站垃圾收集或伺服器垃圾收集](../../standard/garbage-collection/workstation-server-gc.md)。 將值設定為`true` ，以使用伺服器垃圾收集。 如需詳細資訊，請參閱[system.object/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

`ThreadPoolMaxThreads`屬性會設定背景工作執行緒集區的執行緒數目上限。 如需詳細資訊，請參閱[執行緒上限](../run-time-config/threading.md#maximum-threads)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

`ThreadPoolMinThreads`屬性會設定背景工作執行緒集區的執行緒數目下限。 如需詳細資訊，請參閱[最小線程](../run-time-config/threading.md#minimum-threads)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a>TieredCompilation

屬性會設定即時（JIT）編譯器是否使用[分層式編譯。](../whats-new/dotnet-core-3-0.md#tiered-compilation) `TieredCompilation` 將值設定為`false` ，以停用階層式編譯。 如需詳細資訊，請參閱[分層式編譯](../run-time-config/compilation.md#tiered-compilation)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

`TieredCompilationQuickJit`屬性會設定 JIT 編譯程式是否使用快速 jit。 將值設為`false`以停用快速 JIT。 如需詳細資訊，請參閱[快速 JIT](../run-time-config/compilation.md#quick-jit)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

`TieredCompilationQuickJitForLoops`屬性會設定 JIT 編譯程式是否針對包含迴圈的方法使用快速 JIT。 將值設定為`true` ，以啟用包含迴圈之方法的快速 JIT。 如需詳細資訊，請參閱[快速 JIT for 迴圈](../run-time-config/compilation.md#quick-jit-for-loops)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a>NuGet 套件

- [PackageReference](#packagereference)
- [AssetTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>PackageReference

此`PackageReference`專案可讓您指定 NuGet 相依性。 例如，您可能想要參考單一封裝，而不是[中繼套件](../packages.md#metapackages)。 `Include` 屬性會指定套件識別碼。 下列範例中的專案檔程式碼片段會參考[system.webserver](https://www.nuget.org/packages/System.Runtime/)封裝。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

如需詳細資訊，請參閱[專案檔中的套件參考](/nuget/consume-packages/package-references-in-project-files)。

### <a name="assettargetfallback"></a>AssetTargetFallback

`AssetTargetFallback`屬性可讓您為專案所參考的專案和專案所使用的 NuGet 套件，指定其他相容的架構版本。 例如，如果您使用`PackageReference`指定封裝相依性，但該套件並未包含與您專案的`TargetFramework`相容的資產，則該`AssetTargetFallback`屬性會開始播放。 所參考封裝的相容性是使用中`AssetTargetFallback`指定的每個目標架構來間隔。

您可以將`AssetTargetFallback`屬性設定為一個或多個[目標 framework 版本](../../standard/frameworks.md#supported-target-framework-versions)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>套件和還原目標

MSBuild 15.1 引進`pack`和`restore`還原 NuGet 套件的目標，做為組建的一部分。 如需這些目標之 MSBuild 屬性的相關資訊， `PackageTargetFallback`包括，請參閱[NuGet 套件和還原為 MSBuild 目標](/nuget/reference/msbuild-targets)。

## <a name="see-also"></a>請參閱

- [MSBuild 架構參考](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [一般 MSBuild 屬性](/visualstudio/msbuild/common-msbuild-project-properties)
- [NuGet 套件的 MSBuild 屬性](/nuget/reference/msbuild-targets#pack-target)
- [NuGet 還原的 MSBuild 屬性](/nuget/reference/msbuild-targets#restore-properties)
- [自訂群組建](/visualstudio/msbuild/customize-your-build)
