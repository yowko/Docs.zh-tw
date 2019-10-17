---
ms.openlocfilehash: 04e5ca41374fc333a31f0422bc2e89f54b3cb049
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393992"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>裝載：已從 Windows 裝載套件組合中移除 AspNetCoreModule V1

從 ASP.NET Core 3.0 開始，Windows 裝載套件組合將不會包含 AspNetCoreModule （ANCM） V1。

ANCM V2 與 ANCM OutOfProcess 回溯相容，建議用於 ASP.NET Core 3.0 應用程式。

如需討論，請參閱[aspnet/AspNetCore # 7095](https://github.com/aspnet/AspNetCore/issues/7095)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

ANCM V1 包含在 Windows 裝載套件組合中。

#### <a name="new-behavior"></a>新的行為

ANCM V1 並未包含在 Windows 裝載套件組合中。

#### <a name="reason-for-change"></a>變更的原因

ANCM V2 與 ANCM OutOfProcess 回溯相容，建議用於 ASP.NET Core 3.0 應用程式。

#### <a name="recommended-action"></a>建議的動作

使用 ANCM V2 搭配 ASP.NET Core 3.0 應用程式。

如果需要 ANCM V1，可以使用 ASP.NET Core 2.1 或 2.2 Windows 裝載套件組合來安裝。

這種變更會中斷 ASP.NET Core 3.0 應用程式：

- 已使用 ANCM V1 與 `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` 明確加入宣告。
- 具有 `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` 的自訂*web.config*檔案。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
