---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901659"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP：標題名稱常量更改為靜態唯讀

從 ASP.NET 酷 3.0 預覽 5<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>中`const`開始`static readonly`，中的欄位從 更改為 。

有關討論，請參閱[點網/阿斯平核心@9514](https://github.com/dotnet/aspnetcore/issues/9514)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

這些欄位過去是`const`。

#### <a name="new-behavior"></a>新的行為

這些欄位現在是`static readonly`。

#### <a name="reason-for-change"></a>更改原因

更改：

* 防止將值嵌入到裝配體邊界之間，從而允許根據需要進行值校正。
* 實現更快的引用相等性檢查。

#### <a name="recommended-action"></a>建議的動作

針對 3.0 重新編譯。 以下列方式使用這些欄位的原始程式碼不能再這樣做：

* 作為屬性參數
* 作為語句`case`中的一`switch`個
* 定義另一個時`const`

要解決突發性更改，請切換到使用自訂的標頭名稱常量或字串文本。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
