---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901580"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>託管：從 Windows 託管捆綁包中刪除的 AspNetCore 模組 V1

從 ASP.NET 酷睿 3.0 開始，Windows 託管捆綁包將不包含 AspNetCore 模組 （ANCM） V1。

ANCM V2 向後相容 ANCM 出進程，建議與 ASP.NET 酷睿 3.0 應用一起使用。

有關討論，請參閱[dotnet/aspnetcore_7095](https://github.com/dotnet/aspnetcore/issues/7095)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

ANCM V1 包含在 Windows 託管捆綁包中。

#### <a name="new-behavior"></a>新的行為

ANCM V1 不包括在 Windows 託管捆綁包中。

#### <a name="reason-for-change"></a>更改原因

ANCM V2 向後相容 ANCM 出進程，建議與 ASP.NET 酷睿 3.0 應用一起使用。

#### <a name="recommended-action"></a>建議的動作

將 ANCM V2 與 ASP.NET核心 3.0 應用一起使用。

如果需要 ANCM V1，可以使用ASP.NET酷睿 2.1 或 2.2 Windows 託管捆綁包進行安裝。

此更改將破壞 ASP.NET Core 3.0 應用：

- 明確選擇將 ANCM V1`<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`與 。
- 使用 具有 自訂*Web.config*檔`<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
