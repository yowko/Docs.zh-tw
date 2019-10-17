---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394328"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP： HeaderNames 常數已變更為靜態 readonly

從 ASP.NET Core 3.0 Preview 5 開始，<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> 中的欄位已從 `const` 變更為 `static readonly`。

如需討論，請參閱[aspnet/AspNetCore # 9514](https://github.com/aspnet/AspNetCore/issues/9514)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

這些欄位可用來 `const`。

#### <a name="new-behavior"></a>新的行為

這些欄位現在 `static readonly`。

#### <a name="reason-for-change"></a>變更的原因

變更：

* 防止跨元件界限內嵌值，以允許視需要進行值更正。
* 啟用更快速的參考相等檢查。

#### <a name="recommended-action"></a>建議的動作

針對3.0 重新編譯。 以下列方式使用這些欄位的原始程式碼不會再這麼做：

* 做為屬性引數
* 做為 `switch` 語句中的 `case`
* 定義另一個 `const` 時

若要解決中斷性變更，請切換至使用自我定義的標頭名稱常數或字串常值。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
