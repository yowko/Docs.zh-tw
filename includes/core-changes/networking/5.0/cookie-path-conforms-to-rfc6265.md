---
ms.openlocfilehash: 7140f6d4cac063088b3663ab98d292104218b542
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465505"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>Cookie 路徑處理現在符合 RFC 6265

[RFC 6265](https://tools.ietf.org/html/rfc6265)中定義的路徑處理演算法是針對 <xref:System.Net.Cookie> 和類別所執行 <xref:System.Net.CookieContainer> 。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="change-description"></a>變更描述

- <xref:System.Net.Cookie.Path>屬性不再需要是要求路徑的前置詞。
- 的預設值和路徑比對 <xref:System.Net.Cookie.Path> 演算法的計算是依照 RFC 6265 的 [5.1.4 一節](https://tools.ietf.org/html/rfc6265#section-5.1.4) 中的定義來執行。

#### <a name="recommended-action"></a>建議的動作

在大多數情況下，您不需要採取任何動作。 但是，如果您的程式碼相依于 <xref:System.Net.Cookie.Path> 驗證，則您必須在程式碼中執行必要的驗證。 如果您的程式碼相依于的預設值計算 <xref:System.Net.Cookie.Path> ，請考慮以手動方式提供值， <xref:System.Net.Cookie.Path> 而不是使用預設值。

#### <a name="category"></a>類別

網路功能

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Cookie?displayProperty=fullName>
- <xref:System.Net.CookieContainer?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Cookie`
- `T:System.Net.CookieContainer`

-->
