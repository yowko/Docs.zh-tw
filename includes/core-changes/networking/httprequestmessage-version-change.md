---
ms.openlocfilehash: b50a108d2efbfd3da0d690cb02537a12f766b26b
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237309"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage 的預設值。版本已變更為1。1 

@No__t-0 屬性的預設值已從2.0 變更為1.1。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0

#### <a name="change-description"></a>變更描述

在 .NET Core 1.0 到2.0 中，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值是1.1。 從 .NET Core 2.1 開始，它已變更為2.1。 

從 .NET Core 3.0 開始，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性傳回的預設版本號碼再次為1.1。
 
#### <a name="recommended-action"></a>建議的動作

如果您的程式碼相依于 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性，則會傳回預設值2.0。

#### <a name="category"></a>Category

網路

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

