---
title: 選取要使用的 .NET Core 版本
description: 了解 .NET Core 如何自動為您的程式尋找及選擇執行階段版本。 此外，本文還會教導您如何強制使用特定版本。
author: adegeo
ms.author: adegeo
ms.date: 03/24/2020
ms.openlocfilehash: faaa638905bb3c8e9cd4c09af83979d90698df3d
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803114"
---
# <a name="select-the-net-core-version-to-use"></a>選取要使用的 .NET Core 版本

本文說明 .NET Core 工具、SDK 和執行階段用於選取版本的原則。 這些原則在執行使用指定版本的應用程式，以及輕鬆升級開發人員和終端使用者電腦之間提供平衡。 這些原則執行下列動作：

- 輕鬆且有效率地部署 .NET Core，包括安全性和可靠性更新。
- 使用最新的工具和命令，且不受目標執行階段影響。

版本選取發生於下列情況：

- 當您執行 SDK 命令時，[SDK 使用最新安裝的版本](#the-sdk-uses-the-latest-installed-version)。
- 當您繫結組件時，[目標 Framework Moniker 定義建置時間 API](#target-framework-monikers-define-build-time-apis)。
- 當您執行 .NET Core 應用程式時，[目標 Framework 相依應用程式向前復原](#framework-dependent-apps-roll-forward)。
- 當您發佈獨立應用程式時，[獨立部署包含選取的執行階段](#self-contained-deployments-include-the-selected-runtime)。

本文件的其餘部分會說明這四個案例。

## <a name="the-sdk-uses-the-latest-installed-version"></a>SDK 使用最新安裝的版本

SDK 命令包含 `dotnet new` 和 `dotnet run`。 .NET Core CLI 針對每個 `dotnet` 命令都必須選擇 SDK 版本。 根據預設，它會使用電腦上最新安裝的 SDK，即使：

- 專案是以 .NET Core 執行階段的舊版為目標。
- .NET Core SDK 的最新版本是預覽版。

您可以利用最新的 SDK 功能和增強功能，同時以舊版 .NET Core 執行階段為目標。 您可以在不同專案上以多個 .NET Core 執行階段版本為目標，並針對所有專案使用相同的 SDK 工具。

在罕見的情況下，您可能需要使用舊版的 SDK。 您可以在 [*global.json* 檔案](../tools/global-json.md)中指定該版本。 「使用最新版」原則表示您只會使用 *global.json* 指定比最新安裝版本更早的 .NET Core SDK 版本。

*global.json* 可能放在檔案階層中的任何地方。 CLI 會從專案目錄向上搜尋，以找到第一個 *global.json*。 您可以根據指定的 *global.json* 在檔案系統中的位置，來控制其所套用的專案。 .NET CLI 會從目前的工作目錄向上反覆巡覽路徑，以搜尋 *global.json* 檔案。 第一個找到的 *global.json* 檔案指定所使用的版本。 如果已安裝該 SDK 版本，則會使用該版本。 如果找不到在*global.js*中指定的 sdk，則 .net CLI 會使用比對[規則](../tools/global-json.md#matching-rules)來選取相容的 sdk，如果找不到，則會失敗。

下列範例示範 *global.json* 語法：

``` json
{
  "sdk": {
    "version": "3.0.0"
  }
}
```

選取 SDK 版本的過程如下：

1. `dotnet` 會從目前的工作目錄向上反覆反向巡覽路徑，以搜尋 *global.json* 檔案。
1. `dotnet` 使用第一個找到的 *global.json* 中指定的 SDK。
1. 如果找不到 *global.json*，`dotnet` 會使用最新安裝的 SDK。

您可以在 *global.json* 一文的[比對規則](../tools/global-json.md#matching-rules)一節中，深入了解如何選取 SDK 版本。

## <a name="target-framework-monikers-define-build-time-apis"></a>目標 Framework Moniker 定義建置時間 API

您可以針對**目標 Framework Moniker** (TFM) 中定義的 API 建置專案。 您會在專案檔中指定[目標 Framework](../../standard/frameworks.md)。 在您的專案檔中設定 `TargetFramework` 項目，如下列範例所示：

``` xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

您可以針對多個 TFM 建置專案。 設定多個目標 Framework 對程式庫較常見，但也可透過應用程式完成。 您會指定 `TargetFrameworks` 屬性 (`TargetFramework` 的複數形式)。 目標 Framework 是以分號分隔，如下列範例所示：

``` xml
<TargetFrameworks>netcoreapp3.0;net47</TargetFrameworks>
```

指定的 SDK 支援一組固定的架構，限制為其隨附執行階段的目標 Framework。 例如，.NET Core 3.0 SDK 包含 .NET Core 3.0 執行時間，這是 `netcoreapp3.0` 目標 framework 的執行。 .Net Core 3.0 SDK 支援 `netcoreapp2.1` 、 `netcoreapp2.2` 、 `netcoreapp3.0` ，但不支援 `netcoreapp3.1` （或更高版本）。 您會安裝 .NET Core 3.1 SDK 來建立 `netcoreapp3.1` 。

.NET Standard 目標 Framework 也限制為 SDK 隨附執行階段的目標 Framework。 .NET Core 3.1 SDK 的上限為 `netstandard2.1` 。 如需詳細資訊，請參閱 [.NET Standard](../../standard/net-standard.md)。

## <a name="framework-dependent-apps-roll-forward"></a>架構相依應用程式向前復原

當您從使用的來源執行應用程式時 [`dotnet run`](../tools/dotnet-run.md) ，從使用的[**framework 相依部署**](../deploying/index.md#publish-runtime-dependent) [`dotnet myapp.dll`](../tools/dotnet.md#description) ，或從與[**framework 相依的可執行檔**](../deploying/index.md#publish-runtime-dependent)使用 `myapp.exe` ， `dotnet` 可執行檔是應用程式的**主機**。

該主機會選擇電腦上最新安裝的修補程式版本。 例如，如果您在專案檔中指定 `netcoreapp3.0`，且 `3.0.2` 是最新安裝的 .NET 執行階段，則會使用 `3.0.2` 執行階段。

如果找不到可接受的 `3.0.*` 版本，則會使用新的 `3.*` 版本。 例如，如果您指定 `netcoreapp3.0` 並只安裝 `3.1.0`，應用程式會使用 `3.1.0` 執行階段來執行。 此行為稱為「次要版本向前復原」。 也不會考慮舊版。 若未安裝可接受的執行階段，應用程式將不會執行。

如果您將目標設為3.0，則幾個使用範例會示範此行為：

- 已指定✔️3.0。 3.0.3 是已安裝的最高修補程式版本。 會使用3.0.3。
- ❌已指定3.0。 沒有 3.0. * 版本已安裝。 2.1.1 是安裝的最高執行時間。 顯示錯誤訊息。
- 已指定✔️3.0。 沒有 3.0. * 版本已安裝。 3.1.0 是安裝的最高執行階段版本。 會使用3.1.0。
- ❌已指定2.0。 未安裝 2.x 版本。 3.0.0 是安裝的最高執行時間。 顯示錯誤訊息。

次要版本向前復原有一個可能會影響終端使用者的副作用。 請考慮下列案例：

1. 應用程式會指定需要3.0。
2. 不過，執行時，不會安裝版本 3.0. *，3.1.0 是。 將使用版本3.1.0。
3. 之後，使用者會安裝3.0.3 並再次執行應用程式，現在將會使用3.0.3。

3.0.3 和3.1.0 的行為可能不同，特別是針對序列化二進位資料等案例。

## <a name="self-contained-deployments-include-the-selected-runtime"></a>獨立部署包含選取的執行階段

您可以將應用程式發佈為[**獨立散發**](../deploying/index.md#publish-self-contained)。 此方法會將 .NET Core 執行階段和程式庫與您的應用程式配套。 獨立部署不會相依於執行階段環境。 執行階段版本選取發生於發佈時，而不是執行時。

發佈過程會選取指定執行階段系列的最新修補程式版本。 例如， `dotnet publish` 如果 .Net core 3.0.3 是 .Net core 3.0 執行時間系列中的最新修補程式版本，則會選取它。 目標 Framework (包括最新安裝的安全性修補程式) 會封裝於應用程式。

如果不符合針對應用程式指定的最低版本，就會發生錯誤。 `dotnet publish` 會繫結至最新的執行階段修補程式版本 (指定的主要.次要版本系列內)。 `dotnet publish` 不支援 `dotnet run` 的向前復原語意。 如需修補程式和獨立部署的詳細資訊，請參閱部署 .NET Core 應用程式中有關[執行階段修補程式選取](../deploying/runtime-patch-selection.md)的文章。

獨立部署可能需要特定修補程式版本。 您可以覆寫專案檔中的最低執行階段修補程式版本 (改為較高或較低版本)，如下列範例所示：

``` xml
<RuntimeFrameworkVersion>3.0.3</RuntimeFrameworkVersion>
```

`RuntimeFrameworkVersion` 項目會覆寫預設版本原則。 針對獨立部署，`RuntimeFrameworkVersion` 會指定「確切」** 的執行階段架構版本。 針對架構相依應用程式，`RuntimeFrameworkVersion` 會指定所需的「最低」** 執行階段架構版本。

## <a name="see-also"></a>另請參閱

- [下載並安裝 .Net Core](../install/index.yml)。
- [如何移除 .Net Core 執行時間和 SDK](../install/remove-runtime-sdk-versions.md)。
