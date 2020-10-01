---
ms.openlocfilehash: d61a3b3dd855d783d7bff7cb74e5b84969e60860
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608040"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET 無法正確進行多部分處理，可能會導致遺失表單資料。

#### <a name="details"></a>詳細資料

在以 .NET Framework 4.7.2 和更早版本為目標的應用程式中，ASP.NET 可能會不正確地剖析多部分界限值，導致在要求執行期間無法使用表單資料。 以 .NET Framework 4.8 或更新版本為目標的應用程式則可正確剖析多部分資料，因此在要求執行期間可使用表單值。

#### <a name="suggestion"></a>建議

從執行 .NET Framework 4.8 的應用程式開始，當使用 <code>targetFrameworkVersion</code> 項目將目標設為 .NET Framework 4.8 或更新版本時，預設行為會變更為去除分隔符號。 當以舊版 Framework 為目標，或不使用 <code>targetFrameworkVersion</code> 時，仍會傳回某些值的尾端分隔符號。您也可以使用 <code>appSetting</code> 明確地控制此行為：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Unknown|
|版本|4.8|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
