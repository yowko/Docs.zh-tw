---
title: 運行時配置選項
description: 瞭解如何使用運行時配置設置配置 .NET Core 應用程式。
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399158"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="e757f-103">.NET 核心運行時配置設置</span><span class="sxs-lookup"><span data-stu-id="e757f-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="e757f-104">.NET Core 支援使用設定檔和環境變數來配置 .NET Core 應用程式在運行時的行為。</span><span class="sxs-lookup"><span data-stu-id="e757f-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="e757f-105">如果：</span><span class="sxs-lookup"><span data-stu-id="e757f-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="e757f-106">您不擁有或控制應用程式的原始程式碼，因此無法以程式設計方式配置它。</span><span class="sxs-lookup"><span data-stu-id="e757f-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="e757f-107">應用程式的多個實例在單個系統上同時運行，並且您希望為每個實例配置以獲得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="e757f-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="e757f-108">本文檔正在進行中。</span><span class="sxs-lookup"><span data-stu-id="e757f-108">This documentation is a work in progress.</span></span> <span data-ttu-id="e757f-109">如果您注意到此處提供的資訊不完整或不准確，請[打開問題](https://github.com/dotnet/docs/issues)以告知我們，或[提交拉取請求](https://github.com/dotnet/docs/pulls)以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="e757f-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="e757f-110">有關提交 dotnet/docs 存儲庫的拉取請求的資訊，請參閱[參與者指南](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)。</span><span class="sxs-lookup"><span data-stu-id="e757f-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="e757f-111">.NET Core 提供了以下用於配置運行時應用程式行為的機制：</span><span class="sxs-lookup"><span data-stu-id="e757f-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="e757f-112">[運行時配置.json 檔](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="e757f-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="e757f-113">MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="e757f-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="e757f-114">環境變數</span><span class="sxs-lookup"><span data-stu-id="e757f-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="e757f-115">某些配置值也可以通過調用<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>方法以程式設計方式設置。</span><span class="sxs-lookup"><span data-stu-id="e757f-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="e757f-116">本文檔本節中的文章按類別組織，例如[調試](debugging-profiling.md)和[垃圾回收](garbage-collector.md)。</span><span class="sxs-lookup"><span data-stu-id="e757f-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="e757f-117">在適用的情況下，將顯示用於運行時*config.json*檔、MSBuild 屬性、環境變數的配置選項，以及用於交叉引用的 .NET Framework 專案的*app.config*檔。</span><span class="sxs-lookup"><span data-stu-id="e757f-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="e757f-118">運行時配置.json</span><span class="sxs-lookup"><span data-stu-id="e757f-118">runtimeconfig.json</span></span>

<span data-ttu-id="e757f-119">[生成](../tools/dotnet-build.md)專案時，在輸出目錄中生成 *[appname]運行時config.json*檔。</span><span class="sxs-lookup"><span data-stu-id="e757f-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="e757f-120">如果*運行時 config.template.json*檔與專案檔案位於同一資料夾中，則它包含的任何配置選項都將合併到 *[appname]運行時config.json*檔中。</span><span class="sxs-lookup"><span data-stu-id="e757f-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="e757f-121">如果要自行構建應用，請將任何配置選項放在*運行時 config.template.json*檔中。</span><span class="sxs-lookup"><span data-stu-id="e757f-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="e757f-122">如果您剛剛運行應用程式，請直接將它們插入 *[應用程式名稱]運行時config.json*檔。</span><span class="sxs-lookup"><span data-stu-id="e757f-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="e757f-123">*[應用程式名稱]運行時config.json*檔將在後續生成上被覆蓋。</span><span class="sxs-lookup"><span data-stu-id="e757f-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="e757f-124">在*運行時 config.json*檔的**配置屬性**部分中指定運行時配置選項。</span><span class="sxs-lookup"><span data-stu-id="e757f-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="e757f-125">本節的形式為：</span><span class="sxs-lookup"><span data-stu-id="e757f-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="e757f-126">示例 [應用程式名稱]運行時配置.json 檔</span><span class="sxs-lookup"><span data-stu-id="e757f-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="e757f-127">如果要將選項放在輸出 JSON 檔中，則將它們嵌套在 屬性下`runtimeOptions`。</span><span class="sxs-lookup"><span data-stu-id="e757f-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="e757f-128">運行時配置.template.json 檔示例</span><span class="sxs-lookup"><span data-stu-id="e757f-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="e757f-129">如果要將選項放在範本 JSON 檔中，則省略該`runtimeOptions`屬性。</span><span class="sxs-lookup"><span data-stu-id="e757f-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="e757f-130">MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="e757f-130">MSBuild properties</span></span>

<span data-ttu-id="e757f-131">可以使用 SDK 樣式 .NET Core 專案的 *.csproj*或 *.vbproj*檔中的 MSBuild 屬性設置某些運行時配置選項。</span><span class="sxs-lookup"><span data-stu-id="e757f-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="e757f-132">MSBuild 屬性優先于*運行時 config.template.json*檔中設置的選項。</span><span class="sxs-lookup"><span data-stu-id="e757f-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="e757f-133">它們還覆蓋您在 *[appname]運行時 config.json*檔中在生成時設置的任何選項。</span><span class="sxs-lookup"><span data-stu-id="e757f-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="e757f-134">下面是一個示例 SDK 風格的專案檔案，其中包含用於配置運行時行為的 MSBuild 屬性：</span><span class="sxs-lookup"><span data-stu-id="e757f-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="e757f-135">用於配置運行時行為的 MSBuild 屬性在每個區域的各個文章中都有說明，例如[垃圾回收](garbage-collector.md)。</span><span class="sxs-lookup"><span data-stu-id="e757f-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="e757f-136">環境變數</span><span class="sxs-lookup"><span data-stu-id="e757f-136">Environment variables</span></span>

<span data-ttu-id="e757f-137">環境變數可用於提供一些運行時配置資訊。</span><span class="sxs-lookup"><span data-stu-id="e757f-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="e757f-138">指定為環境變數的配置旋鈕通常具有首碼**COMPlus_**。</span><span class="sxs-lookup"><span data-stu-id="e757f-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="e757f-139">您可以在命令列的 Windows 控制台中定義環境變數，也可以通過在 Windows 和基於 Unix 的系統上調用<xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType>該方法來以程式設計方式定義環境變數。</span><span class="sxs-lookup"><span data-stu-id="e757f-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="e757f-140">以下示例演示如何在命令列設置環境變數：</span><span class="sxs-lookup"><span data-stu-id="e757f-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
