---
ms.openlocfilehash: 78d2ec6fb505573ad36d55a9ca0a20452b7fa244
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002886"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage 的預設值。版本已變更為1。1 

@No__t-0 屬性的預設值已從2.0 變更為1.1。

#### <a name="version-introduced"></a>引進的版本

.NET Core 3.0

#### <a name="details"></a>詳細資料

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

