---
ms.openlocfilehash: 4a916a4178535763712ebd58fde1a81e456da0d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538811"
---
### <a name="directorypackagesprops-files-is-imported-by-default"></a>.Props 檔案預設會匯入

NuGet 的 *.props* 檔案會自動匯入名為 *.props* 的檔案（如果在專案資料夾或其任何祖系中找到）。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中，您的專案檔中可能會有一個名為 *.props* 的檔案，而且在組建時，NuGet 的 *.props* 檔案不會自動匯入該檔案。

從 .NET 5.0 開始，如果檔案存在於專案資料夾或任何祖系中， *就* 會自動匯入這類檔案。 如果您的專案資料夾中有此名稱的檔案，此自動匯入可能會變更組建的行為。 例如，檔案會匯入，但不是之前，如果您明確匯入，則可能會變更匯入的順序。

#### <a name="reason-for-change"></a>變更的原因

這項變更的目的是為了支援 NuGet 的 [中央套件版本](https://github.com/NuGet/Home/wiki/Centrally-managing-NuGet-package-versions) 設定。

#### <a name="recommended-action"></a>建議的動作

重新命名現有的 *.props* 檔案（如果不應自動匯入的話）。

#### <a name="category"></a>類別

MSBuild

#### <a name="affected-apis"></a>受影響的 API

N/A

<!--

#### Affected APIs

Not detectable via API analysis.

-->
