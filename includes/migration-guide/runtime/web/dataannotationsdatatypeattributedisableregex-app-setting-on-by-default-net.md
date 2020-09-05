---
ms.openlocfilehash: 0d38e2177377e7e9ea911071eb65aa13aa1f5900
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497477"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>"dataAnnotations:dataTypeAttribute:disableRegEx" 應用程式設定，在 .NET Framework 4.7.2 中預設會開啟

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.1 中，提供了應用程式設定 (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>)，可讓使用者能停用在資料類型屬性 (例如 <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>、<xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> 及 <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>) 中使用規則運算式。 如此有助於降低安全性弱點，例如避免發生使用特定規則運算式的拒絕服務攻擊之可能性。<br/>在 .NET Framework 4.6.1 中，停用使用 RegEx 的此應用程式設定，預設會設為 <code>false</code>。 從 .NET Framework 4.7.2 開始，此設定參數預設會設定為， <code>true</code> 以進一步降低以 .NET Framework 4.7.2 和更新版本為目標之 web 應用程式的安全性漏洞。

#### <a name="suggestion"></a>建議

若您發現您 Web 應用程式中的規則運算式，在升級至 .NET Framework 4.7.2 之後無法運作，可將 <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> 設定的值，更新為 <code>false</code>，以還原為先前的行為。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.7.2|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
