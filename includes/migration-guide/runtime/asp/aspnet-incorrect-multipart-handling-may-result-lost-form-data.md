---
ms.openlocfilehash: 6a99ed916e4e86e85d7ebc2d6ea36a6372c00206
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802678"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a>ASP.NET 無法正確進行多部分處理，可能會導致遺失表單資料。

|   |   |
|---|---|
|詳細資料|在目標為 .NET Framework 4.7.2 和更早版本的應用程式中，ASP.Net 可能無法正確剖析多部分界限值，而導致要求執行期間無法使用表單資料。 以 .NET Framework 4.8 或更新版本為目標的應用程式則可正確剖析多部分資料，因此在要求執行期間可使用表單值。|
|建議|從執行 .NET Framework 4.8 的應用程式開始，當使用 <code>targetFrameworkVersion</code> 項目將目標設為 .NET Framework 4.8 或更新版本時，預設行為會變更為去除分隔符號。 當以舊版 Framework 為目標，或不使用 <code>targetFrameworkVersion</code> 時，仍會傳回某些值的尾端分隔符號。您也可以使用 <code>appSetting</code> 明確地控制此行為：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|範圍|不明|
|版本|4.8|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

