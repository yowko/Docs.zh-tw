---
ms.openlocfilehash: fdbe8ca9b6dbf24c08a2d041c5c7f2e869995f69
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414446"
---
### <a name="cookie-path-handling-now-conforms-to-rfc-6265"></a>Cookie 路徑處理現在符合 RFC 6265

[RFC 6265](https://tools.ietf.org/html/rfc6265)中定義的路徑處理演算法已針對 `Cookie` 和 `CookieContainer` 類別實作為。

#### <a name="version-introduced"></a>引進的版本

5.0

#### <a name="change-description"></a>變更描述

- 將 `Path` 會移除此屬性的限制， (不會再是要求路徑) 的前置詞。
- 的預設值和路徑比對演算法的計算 `Path` 是依照 RFC 6265 的 [5.1.4 一節](https://tools.ietf.org/html/rfc6265#section-5.1.4) 中的定義來執行。

#### <a name="recommended-action"></a>建議的動作

在大多數情況下，您不需要採取任何動作。 但是，如果您的程式碼相依于 `Path` 驗證，則您必須在程式碼中執行必要的驗證; 或者，如果您的程式碼相依于 `Path` 的預設值計算，您可能會想要 `Path` 手動提供值，而不是使用預設值。

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
