---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901580"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>裝載：已從 Windows 裝載套件組合移除 AspNetCoreModule V1

從 ASP.NET Core 3.0 開始，Windows 裝載套件組合將不會包含 AspNetCoreModule (ANCM) V1。

ANCM V2 可回溯相容于 ANCM OutOfProcess，並建議搭配 ASP.NET Core 3.0 應用程式使用。

如需討論，請參閱 [dotnet/aspnetcore # 7095](https://github.com/dotnet/aspnetcore/issues/7095)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

ANCM V1 包含在 Windows 裝載套件組合中。

#### <a name="new-behavior"></a>新的行為

ANCM V1 未包含在 Windows 裝載套件組合中。

#### <a name="reason-for-change"></a>變更的原因

ANCM V2 可回溯相容于 ANCM OutOfProcess，並建議搭配 ASP.NET Core 3.0 應用程式使用。

#### <a name="recommended-action"></a>建議的動作

使用 ANCM V2 搭配 ASP.NET Core 3.0 應用程式。

如果需要 ANCM V1，可以使用 ASP.NET Core 2.1 或 2.2 Windows 裝載套件組合來安裝。

這種變更將會中斷下列 ASP.NET Core 3.0 應用程式：

- 明確選擇使用 ANCM V1 搭配 `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` 。
- 使用自訂的 *web.config* 檔案 `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
