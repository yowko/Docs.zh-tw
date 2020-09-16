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
# <a name="net-core-run-time-configuration-settings"></a>.NET Core 執行時間設定

.NET Core 支援使用設定檔和環境變數，在執行時間設定 .NET Core 應用程式的行為。 如果有下列情況，則執行時間設定是一個很好用的選項：

- 您不會擁有或控制應用程式的原始程式碼，因此無法以程式設計方式進行設定。

- 您應用程式的多個實例會在單一系統上同時執行，而且您想要設定每個實例以獲得最佳效能。

> [!NOTE]
> 本檔是進行中的工作。 如果您注意到此處所呈現的資訊不完整或不正確，請 [開啟問題](https://github.com/dotnet/docs/issues) 讓我們知道，或 [提交提取要求](https://github.com/dotnet/docs/pulls) 來解決問題。 如需提交 dotnet/檔儲存機制提取要求的相關資訊，請參閱《 [參與者指南》](/contribute/dotnet/dotnet-contribute)。

.NET Core 提供下列機制來設定執行時間的應用程式行為：

- 檔案 [ 上的runtimeconfig.js](#runtimeconfigjson)

- [MSBuild 屬性](#msbuild-properties)

- [環境變數](#environment-variables)

> [!TIP]
> 使用環境變數設定執行時間選項會將設定套用至所有 .NET Core 應用程式。 在 *runtimeconfig.json* 或 project 檔中設定執行時間選項，只會將設定套用至該應用程式。

某些設定值也可以透過呼叫方法，以程式設計方式設定 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 。

本檔的這一節中的文章是依類別目錄組織，例如， [調試](debugging-profiling.md) 程式和 [垃圾收集](garbage-collector.md)。 在適用的情況下，會針對檔案、MSBuild 屬性、環境變數和 .NET Framework 專案的交互參照*app.config*檔案，顯示*runtimeconfig.js*的設定選項。

## <a name="runtimeconfigjson"></a>runtimeconfig.js開啟

[建立](../tools/dotnet-build.md)專案時，會在輸出目錄中產生檔案的 *[appname] .runtimeconfig.js* 。 如果檔案 *runtimeconfig.template.js* 存在於與專案檔相同的資料夾中，其包含的任何設定選項都會合並到檔案的 *[appname] .runtimeconfig.js* 中。 如果您要自行建立應用程式，請將任何設定選項放在 *runtimeconfig.template.js* 檔案中。 如果您只是執行應用程式，請將它們直接插入檔案中的 *[appname] .runtimeconfig.js* 。

> [!NOTE]
> 檔案上的 *[appname] .runtimeconfig.js* 將會在後續的組建中遭到覆寫。

在檔案*runtimeconfig.js*的 [ **configProperties** ] 區段中指定執行時間設定選項。 此區段的格式如下：

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>檔案上的範例 [appname] .runtimeconfig.js

如果您要將選項放在輸出 JSON 檔案中，請將它們放在 `runtimeOptions` 屬性之下。

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

### <a name="example-runtimeconfigtemplatejson-file"></a>檔案 runtimeconfig.template.js範例

如果您要將選項放在範本 JSON 檔案中，請省略 `runtimeOptions` 屬性。

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a>MSBuild 屬性

您可以使用 SDK 樣式之 .NET Core 專案的 *.csproj* 或 *vbproj* 檔案中的 MSBuild 屬性來設定某些執行時間設定選項。 MSBuild 屬性優先于在檔案的 *runtimeconfig.template.js* 中設定的選項。 它們也會覆寫您在組建階段于檔案的 *[appname] .runtimeconfig.js* 中設定的任何選項。

以下是範例 SDK 樣式的專案檔，其中包含用來設定執行時間行為的 MSBuild 屬性：

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

用於設定執行時間行為的 MSBuild 屬性，會在每個區域的個別文章中注明，例如 [垃圾收集](garbage-collector.md)。 它們也會列在 SDK 樣式專案的 MSBuild 屬性參考的 [ [執行時間](../project-sdk/msbuild-props.md#run-time-configuration-properties) 設定] 區段中。

## <a name="environment-variables"></a>環境變數

環境變數可以用來提供一些執行時間設定資訊。 使用環境變數設定執行時間選項會將設定套用至所有 .NET Core 應用程式。 指定為環境變數的設定旋鈕通常會有 **COMPlus_** 的前置詞。

您可以從 Windows 主控台、命令列或以程式設計方式，在 <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> windows 和 Unix 系統上呼叫方法，來定義環境變數。

下列範例示範如何在命令列設定環境變數：

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
