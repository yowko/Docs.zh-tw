---
ms.openlocfilehash: 4daa08ce4bbcfe5a7242f19506811e422d0477b7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760722"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>"dataAnnotations:dataTypeAttribute:disableRegEx" 應用程式設定，在 .NET Framework 4.7.2 中預設會開啟

|   |   |
|---|---|
|詳細資料|在 .NET Framework 4.6.1 中，提供了應用程式設定 (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>)，可讓使用者能停用在資料類型屬性 (例如 <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>、<xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> 及 <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>) 中使用規則運算式。 如此有助於降低安全性弱點，例如避免發生使用特定規則運算式的拒絕服務攻擊之可能性。<br/>在 .NET Framework 4.6.1 中，停用使用 RegEx 的此應用程式設定，預設會設為 <code>false</code>。 從 .NET Framework 4.7.2 開始，此組態參數預設會設為 <code>true</code>，以進一步降低鎖定 .NET Framework 4.7.2 及更新版本為目標的 Web 應用程式之安全弱點。|
|建議|若您發現您 Web 應用程式中的規則運算式，在升級至 .NET Framework 4.7.2 之後無法運作，可將 <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> 設定的值，更新為 <code>false</code>，以還原為先前的行為。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appsettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appsettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.2|
|類型|執行階段|

