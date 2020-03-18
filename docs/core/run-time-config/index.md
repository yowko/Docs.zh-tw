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
# <a name="net-core-run-time-configuration-settings"></a>.NET 核心運行時配置設置

.NET Core 支援使用設定檔和環境變數來配置 .NET Core 應用程式在運行時的行為。 如果：

- 您不擁有或控制應用程式的原始程式碼，因此無法以程式設計方式配置它。

- 應用程式的多個實例在單個系統上同時運行，並且您希望為每個實例配置以獲得最佳性能。

> [!NOTE]
> 本文檔正在進行中。 如果您注意到此處提供的資訊不完整或不准確，請[打開問題](https://github.com/dotnet/docs/issues)以告知我們，或[提交拉取請求](https://github.com/dotnet/docs/pulls)以解決此問題。 有關提交 dotnet/docs 存儲庫的拉取請求的資訊，請參閱[參與者指南](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)。

.NET Core 提供了以下用於配置運行時應用程式行為的機制：

- [運行時配置.json 檔](#runtimeconfigjson)

- [MSBuild 屬性](#msbuild-properties)

- [環境變數](#environment-variables)

某些配置值也可以通過調用<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>方法以程式設計方式設置。

本文檔本節中的文章按類別組織，例如[調試](debugging-profiling.md)和[垃圾回收](garbage-collector.md)。 在適用的情況下，將顯示用於運行時*config.json*檔、MSBuild 屬性、環境變數的配置選項，以及用於交叉引用的 .NET Framework 專案的*app.config*檔。

## <a name="runtimeconfigjson"></a>運行時配置.json

[生成](../tools/dotnet-build.md)專案時，在輸出目錄中生成 *[appname]運行時config.json*檔。 如果*運行時 config.template.json*檔與專案檔案位於同一資料夾中，則它包含的任何配置選項都將合併到 *[appname]運行時config.json*檔中。 如果要自行構建應用，請將任何配置選項放在*運行時 config.template.json*檔中。 如果您剛剛運行應用程式，請直接將它們插入 *[應用程式名稱]運行時config.json*檔。

> [!NOTE]
> *[應用程式名稱]運行時config.json*檔將在後續生成上被覆蓋。

在*運行時 config.json*檔的**配置屬性**部分中指定運行時配置選項。 本節的形式為：

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>示例 [應用程式名稱]運行時配置.json 檔

如果要將選項放在輸出 JSON 檔中，則將它們嵌套在 屬性下`runtimeOptions`。

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

### <a name="example-runtimeconfigtemplatejson-file"></a>運行時配置.template.json 檔示例

如果要將選項放在範本 JSON 檔中，則省略該`runtimeOptions`屬性。

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

可以使用 SDK 樣式 .NET Core 專案的 *.csproj*或 *.vbproj*檔中的 MSBuild 屬性設置某些運行時配置選項。 MSBuild 屬性優先于*運行時 config.template.json*檔中設置的選項。 它們還覆蓋您在 *[appname]運行時 config.json*檔中在生成時設置的任何選項。

下面是一個示例 SDK 風格的專案檔案，其中包含用於配置運行時行為的 MSBuild 屬性：

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

用於配置運行時行為的 MSBuild 屬性在每個區域的各個文章中都有說明，例如[垃圾回收](garbage-collector.md)。

## <a name="environment-variables"></a>環境變數

環境變數可用於提供一些運行時配置資訊。 指定為環境變數的配置旋鈕通常具有首碼**COMPlus_**。

您可以在命令列的 Windows 控制台中定義環境變數，也可以通過在 Windows 和基於 Unix 的系統上調用<xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType>該方法來以程式設計方式定義環境變數。

以下示例演示如何在命令列設置環境變數：

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
