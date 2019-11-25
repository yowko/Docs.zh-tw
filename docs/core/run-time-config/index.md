---
title: 執行時間設定
description: 瞭解如何使用執行時間設定設定來設定 .NET Core 應用程式。
ms.date: 11/13/2019
ms.openlocfilehash: f7074b07bdd5aca23b6caae78952d630d905c489
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283986"
---
# <a name="net-core-run-time-configuration-settings"></a>.NET Core 執行時間設定

.NET Core 支援使用設定檔和環境變數，在執行時間設定 .NET Core 應用程式的行為。 在下列情況中，執行時間設定是一個吸引人的選項：

- 您不會擁有或控制應用程式的原始程式碼，因此無法以程式設計方式進行設定。

- 應用程式的多個實例會在單一系統上同時執行，而您想要設定每個實例以獲得最佳效能。

> [!NOTE]
> 本檔是進行中的工作。 如果您發現此處顯示的資訊不完整或不正確，請[開啟問題](https://github.com/dotnet/docs/issues)讓我們知道，或[提交提取要求](https://github.com/dotnet/docs/pulls)以解決問題。 如需提交 dotnet/檔存放庫之提取要求的相關資訊，請參閱[參與者指南](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)。

.NET Core 提供下列機制，讓您在執行時間設定應用程式：

- [.Runtimeconfig.json json](#runtimeconfigjson)檔案

- [環境變數](#environment-variables)

檔集的這一節中的文章包含依類別目錄進行組織，例如，「偵測」和「垃圾收集」。 *.Runtimeconfig.json*會顯示可用的設定選項： [僅限 .net Core）]、[app.config （僅限 .NET Framework）]*和 [環境*變數]。

## <a name="runtimeconfigjson"></a>.runtimeconfig.json json

在 *.runtimeconfig.json*檔案的**configProperties**區段中，指定執行時間設定選項。 本節的格式如下：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

以下是範例檔案：

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

[Dotnet build](../tools/dotnet-build.md)命令會在組建目錄中自動建立 *.runtimeconfig.json*檔案。 當您在 Visual Studio 中選取 [**建立**] 功能表選項時，也會建立此檔案。 之後，您就可以在檔案建立後加以編輯。

某些設定值也可以藉由呼叫 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 方法，以程式設計方式進行設定。

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
