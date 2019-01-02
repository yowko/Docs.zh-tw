---
title: 適用於 .NET Core 獨立式應用程式部署的執行階段向前復原。
description: 了解獨立式部署的 dotnet publish 變更。
author: KathleenDollard
ms.date: 05/31/2018
ms.custom: seodec18
ms.openlocfilehash: 9af1454ede03b277f9b1a10e1d99a997e38809ea
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656293"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>獨立式部署執行階段向前復原

.NET Core [獨立式應用程式部署](index.md)包含 .NET Core l 程式庫和 .NET Core 執行階段。 從 NET Core 2.1 SDK (版本 2.1.300) 開始，獨立式應用程式部署[會發佈電腦上的最高修補程式執行階段](https://github.com/dotnet/designs/pull/36)。 根據預設，用於獨立式部署的 [`dotnet publish`](../tools/dotnet-publish.md) 會選取發佈電腦上已安裝為 SDK 一部分的最新版本。 這可讓您部署的應用程式使用 `publish` 期間所提供的安全性修正 (和其他修正) 來執行。 應用程式必須重新發佈，才能取得新的修補程式。 藉由在 `dotnet publish` 命令上指定 `-r <RID>`，或者在專案檔 (csproj / vbproj) 中或命令列上指定[執行階段識別碼 (RID)](../rid-catalog.md)，即可建立獨立式應用程式。

## <a name="patch-version-roll-forward-overview"></a>修補程式版本向前復原概觀

[`restore`](../tools/dotnet-restore.md)、[`build`](../tools/dotnet-build.md) 和 [`publish`](../tools/dotnet-publish.md) 是可以分別執行的 `dotnet` 命令。 執行階段選擇屬於 `restore` 作業的一部分，而不是 `publish` 或 `build`。 如果您呼叫 `publish`，將會選擇最新的修補程式版本。 如果您呼叫 `publish` 搭配 `--no-restore` 引數，則可能無法取得所需的修補程式版本，因為之前的 `restore` 可能尚未使用新的獨立式應用程式發佈原則來執行。 在此情況下，會產生文字類似於下列內容的建置錯誤：

  「此專案已使用 Microsoft.NETCore.App 2.0.0　版進行還原，但以目前的設定，將改用 2.0.6 版。 若要解決此問題，請確定會針對還原和後續作業 (例如建置或發佈) 使用相同的設定。 一般來說，如果在建置或發佈期間 (而不是在還原期間) 設定了 RuntimeIdentifier 屬性，就會發生此問題。」

> [!NOTE]
> `restore` 和 `build` 可以當作另一個命令 (如 `publish`) 的一部分隱含執行。 作為另一個命令的一部分以隱含方式執行時，會提供其他內容給它們，以便產生正確的成品。 當您搭配執行階段進行 `publish` (例如，`dotnet publish -r linux-x64`)，隱含的 `restore` 會還原 linux-x64 執行階段的套件。 如果您明確地呼叫 `restore`，預設不會還原執行階段套件，因為它並沒有該內容。

## <a name="how-to-avoid-restore-during-publish"></a>如何避免在發佈期間進行還原

執行 `restore` 作為 `publish` 作業的一部分有時候可能不適用於您的情況。 若要在建立獨立式應用程式時避免在 `publish` 期間進行 `restore`，請執行下列動作：

* 將 `RuntimeIdentifiers` 屬性設定為要發佈之所有 [RID](../rid-catalog.md) 的分號分隔清單。
* 將 `TargetLatestRuntimePatch` 屬性設定為 `true`。

## <a name="no-restore-argument-with-dotnet-publish-options"></a>No-restore 引數搭配 dotnet publish 選項

如果您想要使用相同的專案檔同時建立獨立式應用程式和[與架構相依的應用程式](index.md)，而且想要使用 `--no-restore` 引數搭配 `dotnet publish`，則選擇下列其中一項：

1. 偏好與架構相依的行為。 如果應用程式是與架構相依的應用程式，這是預設行為。 如果應用程式是獨立式應用程式，且可以使用未修補的 2.1.0 本機執行階段，請在專案檔中將 `TargetLatestRuntimePatch` 設定為 `false`。

2. 偏好獨立式行為。 如果應用程式是獨立式應用程式，這是預設行為。 如果應用程式是與架構相依的應用程式，且需要安裝最新的修補程式，請在專案檔中將 `TargetLatestRuntimePatch` 設定為 `true`。

3. 在專案檔中將 `RuntimeFrameworkVersion` 設定為特定的修補程式版本，藉以取得執行階段架構版本的明確控制權。
