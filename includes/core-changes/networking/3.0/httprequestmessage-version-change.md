---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451876"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>HTTPRequestMessage.Version 的預設值更改為 1.1

屬性的<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>預設值從 2.0 更改為 1.1。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="change-description"></a>變更描述

在 .NET Core 1.0 到 2.0<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>中，該屬性的預設值為 1.1。 從 .NET 核心 2.1 開始，它更改為 2.1。

從 .NET Core 3.0 開始，屬性返回的<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>預設版本號再次為 1.1。

#### <a name="recommended-action"></a>建議的動作

如果代碼依賴于返回預設值 2.0 的屬性，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>則更新代碼。

#### <a name="category"></a>類別

網路功能

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
