---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901659"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP： HeaderNames 常數已變更為靜態 readonly

從 ASP.NET Core 3.0 Preview 5 開始，中的欄位 <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> 已從變更 `const` 為 `static readonly` 。

如需討論，請參閱 [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

這些欄位是用來做為 `const` 。

#### <a name="new-behavior"></a>新的行為

這些欄位現在是 `static readonly` 。

#### <a name="reason-for-change"></a>變更的原因

變更：

* 防止將值內嵌在元件界限上，以便在需要時進行值修正。
* 可加快參考相等檢查的速度。

#### <a name="recommended-action"></a>建議的動作

針對3.0 重新編譯。 以下列方式使用這些欄位的原始程式碼，將無法再執行此動作：

* 做為屬性引數
* 做為 `case` 語句中 `switch` 的
* 定義其他 `const`

若要解決重大變更，請切換到使用自我定義的標頭名稱常數或字串常值。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
