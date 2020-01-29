---
title: 執行時間設定選項
description: 瞭解如何使用執行時間設定設定來設定 .NET Core 應用程式。
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733446"
---
# <a name="net-core-run-time-configuration-settings"></a>.NET Core 執行時間設定

.NET Core 支援使用設定檔和環境變數，在執行時間設定 .NET Core 應用程式的行為。 在下列情況中，執行時間設定是一個吸引人的選項：

- 您不會擁有或控制應用程式的原始程式碼，因此無法以程式設計方式進行設定。

- 應用程式的多個實例會在單一系統上同時執行，而您想要設定每個實例以獲得最佳效能。

> [!NOTE]
> 本檔是進行中的工作。 如果您發現此處顯示的資訊不完整或不正確，請[開啟問題](https://github.com/dotnet/docs/issues)讓我們知道，或[提交提取要求](https://github.com/dotnet/docs/pulls)以解決問題。 如需提交 dotnet/檔存放庫之提取要求的相關資訊，請參閱[參與者指南](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)。

.NET Core 提供下列機制來設定執行時間應用程式行為：

- [.Runtimeconfig.json json](#runtimeconfigjson)檔案

- [MSBuild 屬性](#msbuild-properties)

- [環境變數](#environment-variables)

某些設定值也可以藉由呼叫 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法，以程式設計方式進行設定。

檔的這一節中的文章是依類別目錄進行組織，例如，「[調試](debugging-profiling.md)程式」和「[垃圾收集](garbage-collector.md)」。 適用時，會顯示 *.runtimeconfig.json*的設定選項、MSBuild 屬性、環境變數，以及用於 .NET Framework 專案之交互參考的*app.config*檔案。

## <a name="runtimeconfigjson"></a>.runtimeconfig.json json

[建立](../tools/dotnet-build.md)專案時，會在輸出目錄中產生 *[appname]. .runtimeconfig.json json*檔案。 如果 *.runtimeconfig.json*與專案檔存在於相同的資料夾中，它所包含的任何設定選項都會合並至 *[appname]. .runtimeconfig.json. json*檔案。 如果您要自行建立應用程式，請將任何設定選項放在 *.runtimeconfig.json*檔案中。 如果您只是執行應用程式，請將它們直接插入 *[appname]. .runtimeconfig.json json*檔案中。

> [!NOTE]
> 後續的組建將會覆寫 *[appname]. .runtimeconfig.json json*檔案。

在 *.runtimeconfig.json*檔案的**configProperties**區段中，指定執行時間設定選項。 本節的格式如下：

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>範例 [appname]. .runtimeconfig.json. json 檔案

如果您要將選項放在輸出 JSON 檔案中，請將它們嵌套在 `runtimeOptions` 屬性底下。

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

### <a name="example-runtimeconfigtemplatejson-file"></a>範例 .runtimeconfig.json. template json 檔案

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

某些執行時間設定選項可以使用 SDK 樣式 .NET Core 專案的 *.csproj*或*vbproj*檔案中的 MSBuild 屬性來設定。 MSBuild 屬性的優先順序高於 *.runtimeconfig.json*中設定的選項。 它們也會覆寫您在組建時于 *[appname]. .runtimeconfig.json. json*檔案中設定的任何選項。

以下是使用 MSBuild 屬性來設定執行時間行為的範例 SDK 樣式專案檔案：

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

設定執行時間行為的 MSBuild 屬性會在每個區域的個別文章中注明，例如[垃圾收集](garbage-collector.md)。

## <a name="environment-variables"></a>環境變數

環境變數可以用來提供一些執行時間設定資訊。 指定為環境變數的設定旋鈕通常會**COMPlus_** 前置詞。

您可以從 Windows [控制台]、命令列或以程式設計方式，在 Windows 和 Unix 系統上呼叫 <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> 方法，以定義環境變數。

下列範例示範如何在命令列設定環境變數：

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
