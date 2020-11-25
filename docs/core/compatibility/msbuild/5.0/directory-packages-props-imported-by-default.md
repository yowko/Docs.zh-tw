---
title: 重大變更： .props 檔案預設會匯入
description: 瞭解 .NET 5.0 中的重大變更，其中 NuGet 的 .props 檔案會自動匯入名為 .props 的檔案（如果在專案資料夾中找到的話）。
ms.date: 09/17/2020
ms.openlocfilehash: ee8a2999b801e81750d96a0bc985e3c8169224a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760642"
---
# <a name="directorypackagesprops-files-is-imported-by-default"></a>.Props 檔案預設會匯入

NuGet 的 *.props* 檔案會自動匯入名為 *.props* 的檔案（如果在專案資料夾或其任何祖系中找到）。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="change-description"></a>變更描述

在舊版的 .NET 中，您的專案檔中可能會有一個名為 *.props* 的檔案，而且在組建時，NuGet 的 *.props* 檔案不會自動匯入該檔案。

從 .NET 5.0 開始，如果檔案存在於專案資料夾或任何祖系中， *就* 會自動匯入這類檔案。 如果您的專案資料夾中有此名稱的檔案，此自動匯入可能會變更組建的行為。 例如，檔案會匯入，但不是之前，如果您明確匯入，則可能會變更匯入的順序。

## <a name="reason-for-change"></a>變更的原因

這項變更的目的是為了支援 NuGet 的 [中央套件版本](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) 設定。

## <a name="recommended-action"></a>建議的動作

重新命名現有的 *.props* 檔案（如果不應自動匯入的話）。

## <a name="affected-apis"></a>受影響的 API

N/A

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
