---
ms.openlocfilehash: d61a3b3dd855d783d7bff7cb74e5b84969e60860
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608040"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="c8e21-101">ASP.NET 無法正確進行多部分處理，可能會導致遺失表單資料。</span><span class="sxs-lookup"><span data-stu-id="c8e21-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

#### <a name="details"></a><span data-ttu-id="c8e21-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c8e21-102">Details</span></span>

<span data-ttu-id="c8e21-103">在以 .NET Framework 4.7.2 和更早版本為目標的應用程式中，ASP.NET 可能會不正確地剖析多部分界限值，導致在要求執行期間無法使用表單資料。</span><span class="sxs-lookup"><span data-stu-id="c8e21-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.NET might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="c8e21-104">以 .NET Framework 4.8 或更新版本為目標的應用程式則可正確剖析多部分資料，因此在要求執行期間可使用表單值。</span><span class="sxs-lookup"><span data-stu-id="c8e21-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c8e21-105">建議</span><span class="sxs-lookup"><span data-stu-id="c8e21-105">Suggestion</span></span>

<span data-ttu-id="c8e21-106">從執行 .NET Framework 4.8 的應用程式開始，當使用 <code>targetFrameworkVersion</code> 項目將目標設為 .NET Framework 4.8 或更新版本時，預設行為會變更為去除分隔符號。</span><span class="sxs-lookup"><span data-stu-id="c8e21-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="c8e21-107">當以舊版 Framework 為目標，或不使用 <code>targetFrameworkVersion</code> 時，仍會傳回某些值的尾端分隔符號。您也可以使用 <code>appSetting</code> 明確地控制此行為：</span><span class="sxs-lookup"><span data-stu-id="c8e21-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="c8e21-108">名稱</span><span class="sxs-lookup"><span data-stu-id="c8e21-108">Name</span></span>    | <span data-ttu-id="c8e21-109">值</span><span class="sxs-lookup"><span data-stu-id="c8e21-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c8e21-110">範圍</span><span class="sxs-lookup"><span data-stu-id="c8e21-110">Scope</span></span>   |<span data-ttu-id="c8e21-111">Unknown</span><span class="sxs-lookup"><span data-stu-id="c8e21-111">Unknown</span></span>|
|<span data-ttu-id="c8e21-112">版本</span><span class="sxs-lookup"><span data-stu-id="c8e21-112">Version</span></span>|<span data-ttu-id="c8e21-113">4.8</span><span class="sxs-lookup"><span data-stu-id="c8e21-113">4.8</span></span>|
|<span data-ttu-id="c8e21-114">類型</span><span class="sxs-lookup"><span data-stu-id="c8e21-114">Type</span></span>|<span data-ttu-id="c8e21-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="c8e21-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="c8e21-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c8e21-116">Affected APIs</span></span>

- <xref:System.Web.HttpRequest.Form?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.Files?displayProperty=nameWithType>
- <xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.HttpRequest.Form`
- `P:System.Web.HttpRequest.Files`
- `P:System.Web.HttpRequest.ContentEncoding`

-->
