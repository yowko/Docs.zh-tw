---
title: .NET Core 版本選取
description: 了解 .NET Core 如何尋找及選擇適合您程式的執行階段版本。
author: billwagner
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: d1b885ebbade4736d5f592d1dc1d4ba25a321a16
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874466"
---
# <a name="net-core-version-selection"></a>.NET Core 版本選取

[!INCLUDE [topic-appliesto-net-core-2plus](../../../includes/topic-appliesto-net-core-2plus.md)]

本文說明 .NET Core 工具、SDK 和執行階段用於選取版本的原則。 這些原則在執行使用指定版本的應用程式，以及輕鬆升級開發人員和終端使用者電腦之間提供平衡。 這些原則執行下列作業：

- 輕鬆且有效率地部署 .NET Core，包括安全性和可靠性更新。
- 使用最新的工具和命令，且不受目標執行階段影響。

版本選取發生於下列情況：

- 當您執行 SDK 命令時，[SDK 使用最新安裝的版本](#the-sdk-uses-the-latest-installed-version)。
- 當您繫結組件時，[目標 Framework Moniker 定義建置時間 API](#target-framework-monikers-define-build-time-apis)。
- 當您執行 .NET Core 應用程式時，[目標 Framework 相依應用程式向前復原](#framework-dependent-apps-roll-forward)。
- 當您發佈獨立應用程式時，[獨立部署包含選取的執行階段](#self-contained-deployments-include-the-selected-runtime)。

本文件的其餘部分會說明這四個案例。

## <a name="the-sdk-uses-the-latest-installed-version"></a>SDK 使用最新安裝的版本

SDK 命令包含 `dotnet new`、`dotnet build` 或 `dotnet run`。 `dotnet` CLI 必須為任何命令選擇 SDK 版本。 根據預設，.NET Core CLI 使用電腦上最新安裝的 SDK。 安裝 .NET Core SDK v2.1.301 時，即使您使用的專案以 .NET Core Runtime 2.0 為目標，您也會使用此版本。 請注意，這對預覽版本和發行版本都適用。 您可以利用最新的 SDK 功能和增強功能，同時以舊版 .NET Core 執行階段為目標。 您可以在不同專案上以多個 .NET Core 執行階段版本為目標，並針對所有專案使用相同的 SDK 工具。

在罕見的情況下，您可能需要使用舊版的 SDK。 您可以在 [*global.json* 檔案](../tools/global-json.md)中指定該版本。 「使用最新版」原則表示您只會使用 *global.json* 指定比最新安裝版本更早的 .NET Core SDK 版本。

*global.json* 可能放在檔案階層中的任何地方。 CLI 會從專案目錄向上搜尋，以找到第一個 *global.json*。 您可以根據指定的 *global.json* 在檔案系統中的位置，來控制其所套用的專案。 .NET CLI 會從目前的工作目錄向上反覆巡覽路徑，以搜尋 *global.json* 檔案。 第一個找到的 *global.json* 檔案指定所使用的版本。 如果安裝該版本，則會使用該版本。 如果找不到 *global.json* 中指定的 SDK，.NET CLI 會向前復原到最新安裝的 SDK。 找不到 *global.json* 檔案時，則會與預設行為相同。

下列範例示範 *global.json* 語法：

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

選取 SDK 版本的過程如下：

1. `dotnet` 會從目前的工作目錄向上反覆反向巡覽路徑，以搜尋 *global.json* 檔案。
1. `dotnet` 使用第一個找到的 *global.json* 中指定的 SDK。
1. 如果找不到 *global.json*，`dotnet` 會使用最新安裝的 SDK。

您可以在 *global.json* 主題的[比對規則](../tools/global-json.md)一節中，深入了解如何選取 SDK 版本。

## <a name="target-framework-monikers-define-build-time-apis"></a>目標 Framework Moniker 定義建置時間 API

您可以針對**目標 Framework Moniker** (TFM) 中定義的 API 建置專案。 您會在專案檔中指定[目標 Framework](../../standard/frameworks.md)。 在您的專案檔中設定 `TargetFramework` 項目，如下列範例所示：

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

您可以針對多個 TFM 建置專案。 設定多個目標 Framework 對程式庫較常見，但也可透過應用程式完成。 您會指定 `TargetFrameworks` 屬性 (`TargetFramework` 的複數形式)。 目標 Framework 是以分號分隔，如下列範例所示：

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

指定的 SDK 支援一組固定的架構，限制為其隨附執行階段的目標 Framework。 例如，.NET Core 2.0 SDK 包含 .NET Core 2.0 執行階段，這是 `netcoreapp2.0` 目標 Framework 的實作。 .NET Core 2.0 SDK 支援 `netcoreapp1.0`、`netcoreapp1.1` 和 `netcoreapp2.0`，但不支援 `netcoreapp2.1` (或更新版本)。 您可以安裝 .NET Core 2.1 SDK 來建置 `netcoreapp2.1`。

.NET Standard 目標 Framework 也限制為 SDK 隨附執行階段的目標 Framework。 .NET Core 2.0 SDK 限制為 `netstandard2.0`。

## <a name="framework-dependent-apps-roll-forward"></a>架構相依應用程式向前復原

您可以透過 [`dotnet run`](../tools/dotnet-run.md) 從原始檔執行應用程式。 `dotnet run` 會同時建置及執行應用程式。 `dotnet` 可執行檔是開發環境中應用程式的**主機**。

該主機會選擇電腦上最新安裝的修補程式版本。 例如，如果您在專案檔中指定 `netcoreapp2.0`，且 `2.0.4` 是最新安裝的 .NET 執行階段，則會使用 `2.0.4` 執行階段。

如果找不到可接受的 `2.0.*` 版本，則會使用新的 `2.*` 版本。 例如，如果您指定 `netcoreapp2.0` 並只安裝 `2.1.0`，應用程式會使用 `2.1.0` 執行階段來執行。 此行為稱為「次要版本向前復原」。 也不會考慮舊版。 若未安裝可接受的執行階段，應用程式將不會執行。

以下是示範此行為的幾個使用方式範例：

- 需要 2.0.4。 2.0.5 是安裝的最高修補程式版本。 使用 2.0.5。
- 需要 2.0.4。 未安裝 2.0.* 版本。 1.1.1 是安裝的最高執行階段版本。 顯示錯誤訊息。
- 需要 2.0.4。 2.0.0 是安裝的最高版本。 顯示錯誤訊息。
- 需要 2.0.4。 未安裝 2.0.* 版本。 2.2.2 是安裝的最高 2.x 執行階段版本。 使用 2.2.2。
- 需要 2.0.4。 未安裝 2.x 版本。 已安裝 3.0.0 (不是目前可用的版本)。 顯示錯誤訊息。

次要版本向前復原有一個可能會影響終端使用者的副作用。 請考慮下列案例：

- 需要 2.0.4。 未安裝 2.0.* 版本。 已安裝 2.2.2。 使用 2.2.2。
- 稍後將安裝 2.0.5。 2.0.5 將用於後續應用程式啟動，而不是 2.2.2。 建議使用所需次要版本而不是更高次要版本的最新修補程式。
- 2.0.5 和 2.2.2 的行為可能不同，特別是針對序列化二進位資料等案例。

## <a name="self-contained-deployments-include-the-selected-runtime"></a>獨立部署包含選取的執行階段

您可以將應用程式發佈為[**獨立散發**](../deploying/index.md#self-contained-deployments-scd)。 此方法會將 .NET Core 執行階段和程式庫與您的應用程式配套。 獨立部署不會相依於執行階段環境。 執行階段版本選取發生於發佈時，而不是執行時。

發佈過程會選取指定執行階段系列的最新修補程式版本。 例如，如果 .NET Core 2.0.4 是 .NET Core 2.0 執行階段系列中的最新修補程式版本，`dotnet publish` 會選取此版本。 目標 Framework (包括最新安裝的安全性修補程式) 會封裝於應用程式。

如果不符合針對應用程式指定的最低版本，就會發生錯誤。 `dotnet publish` 會繫結至最新的執行階段修補程式版本 (指定的主要.次要版本系列內)。 `dotnet publish` 不支援 `dotnet run` 的向前復原語意。 如需修補程式和獨立部署的詳細資訊，請參閱部署 .NET Core 應用程式中有關[執行階段修補程式選取](../deploying/runtime-patch-selection.md)的文章。

獨立部署可能需要特定修補程式版本。 您可以覆寫專案檔中的最低執行階段修補程式版本 (改為較高或較低版本)，如下列範例所示：

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` 項目會覆寫預設版本原則。 針對獨立部署，`RuntimeFrameworkVersion` 會指定「確切」的執行階段架構版本。 針對架構相依應用程式，`RuntimeFrameworkVersion` 會指定所需的「最低」執行階段架構版本。
