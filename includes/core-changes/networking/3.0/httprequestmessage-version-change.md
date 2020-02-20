---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451876"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HttpRequestMessage 的預設值。版本已變更為1.1

<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值已從2.0 變更為1.1。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="change-description"></a>變更描述

在 .NET Core 1.0 到2.0 中，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值是1.1。 從 .NET Core 2.1 開始，它已變更為2.1。

從 .NET Core 3.0 開始，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性傳回的預設版本號碼再次為1.1。

#### <a name="recommended-action"></a>建議的動作

更新您的程式碼（如果它相依于傳回預設值2.0 的 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性）。

#### <a name="category"></a>類別

網路功能

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
