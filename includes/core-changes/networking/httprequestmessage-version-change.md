---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198371"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage 的預設值。版本已變更為1。1

<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值已從2.0 變更為1.1。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0

#### <a name="change-description"></a>變更描述

在 .NET Core 1.0 到2.0 中，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值是1.1。 從 .NET Core 2.1 開始，它已變更為2.1。

從 .NET Core 3.0 開始，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性傳回的預設版本號碼再次為1.1。

#### <a name="recommended-action"></a>建議的動作

更新您的程式碼（如果它相依于傳回預設值2.0 的 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性）。

#### <a name="category"></a>Category

網路功能

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

