---
title: ".NET Core 發佈封裝"
description: "了解如何封裝、命名以及建立 .NET Core 版本以進行發佈。"
keywords: ".NET, .NET Core, 來源, 組建"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 71b9d722-c5a8-4271-9ce1-d87e7ae2494d
ms.workload: dotnetcore
ms.openlocfilehash: 9f5cd2f7c4fec553dfdfaf1765663b6896b3061d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-distribution-packaging"></a>.NET Core 發佈封裝

隨著 .NET Core 可在越來越多的平台上使用，了解如何封裝、命名和建立 .NET Core 版本是有用的。 如此一來，套件維護人員可以協助確保一致的體驗，無論使用者選擇在何處執行 .NET。

## <a name="net-core-components"></a>.NET Core 元件

.NET Core 是由三個必須封裝的主要部分組成：

1. **主機** (也稱為"muxer") 有兩個不同的角色：啟用執行階段以啟動應用程式，以及啟用 SDK 來分派命令給它。 主機是原生可執行檔 (`dotnet.exe`) 和其支援的原則文件庫 (安裝在 `host/fxr` 中)。 它是以 [`dotnet/core-setup`](https://github.com/dotnet/core-setup/) 存放庫中的程式碼建置。 在指定的電腦上通常只有一個主機，雖然這不是嚴格要求。
2. **架構**是由執行階段和支援的 Managed 程式庫組成。 該架構可以作為應用程式的一部分安裝，也可以作為可由多個應用程式重複使用之中央位置的共用架構來安裝。 在指定的電腦上可能會安裝任意數目的共用架構。 共用架構位在 `shared/Microsoft.NETCore.App/<version>` 下。 主機會在所有更新程式版本上向前復原。 如果應用程式以 `Microsoft.NETCore.App` 1.0.0 為目標，而只存在 1.0.4，則應用程式將針對 1.0.4 啟動。
3. **SDK** (也稱為「工具」) 是一組受管理的工具，可用來撰寫及建置 .NET Core 程式庫和應用程式。 SDK 包含 CLI、MSBuild，以及相關聯的建置工作與目標、NuGet，新的專案範本等。電腦上可以有多個 SDK (例如，建置明確要求較舊版本的專案)，但建議使用最新發行的工具。

## <a name="recommended-package-names"></a>建議的套件名稱

下列指導方針是套件名稱的建議。 套件維護人員可能會根據各種原因而選擇不遵循建議，例如他們設為目標之特定發佈的不同傳統。

### <a name="minimum-package-set"></a>最小封裝集合

* `dotnet-runtime-[major].[minor]`：指定版本的共用架構 (針對指定的主要 + 次要組合，封裝管理員中僅可使用最新的更新程式版本)。 **相依性**：`dotnet-host`
* `dotnet-sdk`：最新的 SDK。 **相依性**：最新的 `dotnet-sdk-[major].[minor]`。
* `dotnet-sdk-[major].[minor]`：指定版本的 SDK。 指定的版本是內含共用架構的最高內含版本，因此使用者可以輕鬆地將 SDK 與共用架構相關聯。 **相依性**：`dotnet-host`，一或多個 `dotnet-runtime-[major].[minor]` (其中一個執行階段是由 SDK 程式碼本身使用，其他執行階段則是供使用者作為目標建置和執行)。
* `dotnet-host`：最新的主機。

#### <a name="preview-versions"></a>預覽版本

套件維護人員可能會決定要包含共用架構和 SDK 的預覽版本。 這些永遠不應該包含在未建立版本的 `dotnet-sdk` 套件中，但可以作為已建立版本的套件發佈，且將其他預覽標記附加到名稱的主要版本和次要版本區段。 例如，可能會有 `dotnet-sdk-2.0-preview-final` 套件。

### <a name="optional-additional-packages"></a>選用的其他套件

某些維護人員可能會選擇提供其他套件，例如：

* `dotnet-lts`：共用架構的最新長期支援 (LTS) 版本。 [LTS 和目前的版本序列](~/docs/core/versions/lts-current.md)會對應 .NET Core 發行的不同步調。 根據使用者希望更新的頻率，他們可以選擇採用一個序列或其他序列。 這也是一個與支援層級相關的概念，因此根據考量的發行套件，不一定會有意義。

## <a name="disk-layout"></a>磁碟配置

安裝 .NET Core 套件時，其目標目的地在磁碟上的相對位置是很重要的。
`dotnet.exe` 主機應該放在 `sdk` 和 `shared` 資料夾旁，其中包含 `dotnet-sdk` SDK 套件已建立版本的內容，以及 `dotnet-runtime` 共用架構套件。

套件內檔案和目錄的磁碟配置已建立版本。 這表示更新至最新的 `dotnet-runtime` 會將新版本與先前的版本並存安裝，降低因更新套件而中斷現有應用程式的可能性。 套件更新不應該移除先前的版本。

## <a name="update-policies"></a>更新原則

當執行 `update` 時，每個套件的行為會如下所示：

* `dotnet-runtime-[major].[minor]`：新的更新程式版本會更新套件，但新的次要版本或主要版本是個別的套件。
* `dotnet-sdk`：`update` 會向前復原主要、次要和更新程式版本。
* `dotnet-sdk-[major].[minor]`：新的更新程式版本會更新套件，但新的次要版本或主要版本是個別的套件。
* `dotnet-lts`：`update` 會向前復原主要、次要和更新程式版本。

本主題說明我們針對封裝 .NET Core 的建議，不過每個發行套件都能自由選擇要提供哪些版本與提供的時間。 例如，重視穩定性勝過最新版本的發行套件，可能會選擇僅發布與 LTS 版本序列符合的版本。