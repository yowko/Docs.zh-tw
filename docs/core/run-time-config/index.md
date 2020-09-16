---
title: 執行時間設定選項
description: 瞭解如何使用執行時間設定設定來設定 .NET Core 應用程式。
ms.date: 01/21/2020
ms.openlocfilehash: 21673a221d0f21202febf4730b955da66132d5f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538194"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="38931-103">.NET Core 執行時間設定</span><span class="sxs-lookup"><span data-stu-id="38931-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="38931-104">.NET Core 支援使用設定檔和環境變數，在執行時間設定 .NET Core 應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="38931-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="38931-105">如果有下列情況，則執行時間設定是一個很好用的選項：</span><span class="sxs-lookup"><span data-stu-id="38931-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="38931-106">您不會擁有或控制應用程式的原始程式碼，因此無法以程式設計方式進行設定。</span><span class="sxs-lookup"><span data-stu-id="38931-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="38931-107">您應用程式的多個實例會在單一系統上同時執行，而且您想要設定每個實例以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="38931-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="38931-108">本檔是進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="38931-108">This documentation is a work in progress.</span></span> <span data-ttu-id="38931-109">如果您注意到此處所呈現的資訊不完整或不正確，請 [開啟問題](https://github.com/dotnet/docs/issues) 讓我們知道，或 [提交提取要求](https://github.com/dotnet/docs/pulls) 來解決問題。</span><span class="sxs-lookup"><span data-stu-id="38931-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="38931-110">如需提交 dotnet/檔儲存機制提取要求的相關資訊，請參閱《 [參與者指南》](/contribute/dotnet/dotnet-contribute)。</span><span class="sxs-lookup"><span data-stu-id="38931-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](/contribute/dotnet/dotnet-contribute).</span></span>

<span data-ttu-id="38931-111">.NET Core 提供下列機制來設定執行時間的應用程式行為：</span><span class="sxs-lookup"><span data-stu-id="38931-111">.NET Core provides the following mechanisms for configuring application behavior at run time:</span></span>

- <span data-ttu-id="38931-112">檔案 [ 上的runtimeconfig.js](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="38931-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="38931-113">MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="38931-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="38931-114">環境變數</span><span class="sxs-lookup"><span data-stu-id="38931-114">Environment variables</span></span>](#environment-variables)

> [!TIP]
> <span data-ttu-id="38931-115">使用環境變數設定執行時間選項會將設定套用至所有 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="38931-115">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="38931-116">在 *runtimeconfig.json* 或 project 檔中設定執行時間選項，只會將設定套用至該應用程式。</span><span class="sxs-lookup"><span data-stu-id="38931-116">Configuring a run-time option in the *runtimeconfig.json* or project file applies the setting to that application only.</span></span>

<span data-ttu-id="38931-117">某些設定值也可以透過呼叫方法，以程式設計方式設定 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="38931-117">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="38931-118">本檔的這一節中的文章是依類別目錄組織，例如， [調試](debugging-profiling.md) 程式和 [垃圾收集](garbage-collector.md)。</span><span class="sxs-lookup"><span data-stu-id="38931-118">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="38931-119">在適用的情況下，會針對檔案、MSBuild 屬性、環境變數和 .NET Framework 專案的交互參照*app.config*檔案，顯示*runtimeconfig.js*的設定選項。</span><span class="sxs-lookup"><span data-stu-id="38931-119">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="38931-120">runtimeconfig.js開啟</span><span class="sxs-lookup"><span data-stu-id="38931-120">runtimeconfig.json</span></span>

<span data-ttu-id="38931-121">[建立](../tools/dotnet-build.md)專案時，會在輸出目錄中產生檔案的 *[appname] .runtimeconfig.js* 。</span><span class="sxs-lookup"><span data-stu-id="38931-121">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="38931-122">如果檔案 *runtimeconfig.template.js* 存在於與專案檔相同的資料夾中，其包含的任何設定選項都會合並到檔案的 *[appname] .runtimeconfig.js* 中。</span><span class="sxs-lookup"><span data-stu-id="38931-122">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="38931-123">如果您要自行建立應用程式，請將任何設定選項放在 *runtimeconfig.template.js* 檔案中。</span><span class="sxs-lookup"><span data-stu-id="38931-123">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="38931-124">如果您只是執行應用程式，請將它們直接插入檔案中的 *[appname] .runtimeconfig.js* 。</span><span class="sxs-lookup"><span data-stu-id="38931-124">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="38931-125">檔案上的 *[appname] .runtimeconfig.js* 將會在後續的組建中遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="38931-125">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="38931-126">在檔案*runtimeconfig.js*的 [ **configProperties** ] 區段中指定執行時間設定選項。</span><span class="sxs-lookup"><span data-stu-id="38931-126">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="38931-127">此區段的格式如下：</span><span class="sxs-lookup"><span data-stu-id="38931-127">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="38931-128">檔案上的範例 [appname] .runtimeconfig.js</span><span class="sxs-lookup"><span data-stu-id="38931-128">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="38931-129">如果您要將選項放在輸出 JSON 檔案中，請將它們放在 `runtimeOptions` 屬性之下。</span><span class="sxs-lookup"><span data-stu-id="38931-129">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="38931-130">檔案 runtimeconfig.template.js範例</span><span class="sxs-lookup"><span data-stu-id="38931-130">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="38931-131">如果您要將選項放在範本 JSON 檔案中，請省略 `runtimeOptions` 屬性。</span><span class="sxs-lookup"><span data-stu-id="38931-131">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="38931-132">MSBuild 屬性</span><span class="sxs-lookup"><span data-stu-id="38931-132">MSBuild properties</span></span>

<span data-ttu-id="38931-133">您可以使用 SDK 樣式之 .NET Core 專案的 *.csproj* 或 *vbproj* 檔案中的 MSBuild 屬性來設定某些執行時間設定選項。</span><span class="sxs-lookup"><span data-stu-id="38931-133">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="38931-134">MSBuild 屬性優先于在檔案的 *runtimeconfig.template.js* 中設定的選項。</span><span class="sxs-lookup"><span data-stu-id="38931-134">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="38931-135">它們也會覆寫您在組建階段于檔案的 *[appname] .runtimeconfig.js* 中設定的任何選項。</span><span class="sxs-lookup"><span data-stu-id="38931-135">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="38931-136">以下是範例 SDK 樣式的專案檔，其中包含用來設定執行時間行為的 MSBuild 屬性：</span><span class="sxs-lookup"><span data-stu-id="38931-136">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="38931-137">用於設定執行時間行為的 MSBuild 屬性，會在每個區域的個別文章中注明，例如 [垃圾收集](garbage-collector.md)。</span><span class="sxs-lookup"><span data-stu-id="38931-137">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="38931-138">它們也會列在 SDK 樣式專案的 MSBuild 屬性參考的 [ [執行時間](../project-sdk/msbuild-props.md#run-time-configuration-properties) 設定] 區段中。</span><span class="sxs-lookup"><span data-stu-id="38931-138">They are also listed in the [Run-time configuration](../project-sdk/msbuild-props.md#run-time-configuration-properties) section of the MSBuild properties reference for SDK-style projects.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="38931-139">環境變數</span><span class="sxs-lookup"><span data-stu-id="38931-139">Environment variables</span></span>

<span data-ttu-id="38931-140">環境變數可以用來提供一些執行時間設定資訊。</span><span class="sxs-lookup"><span data-stu-id="38931-140">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="38931-141">使用環境變數設定執行時間選項會將設定套用至所有 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="38931-141">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="38931-142">指定為環境變數的設定旋鈕通常會有 **COMPlus_** 的前置詞。</span><span class="sxs-lookup"><span data-stu-id="38931-142">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="38931-143">您可以從 Windows 主控台、命令列或以程式設計方式，在 <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> windows 和 Unix 系統上呼叫方法，來定義環境變數。</span><span class="sxs-lookup"><span data-stu-id="38931-143">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="38931-144">下列範例示範如何在命令列設定環境變數：</span><span class="sxs-lookup"><span data-stu-id="38931-144">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
