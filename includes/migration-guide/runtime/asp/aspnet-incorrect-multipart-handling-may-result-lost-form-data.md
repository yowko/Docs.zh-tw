---
ms.openlocfilehash: 6a99ed916e4e86e85d7ebc2d6ea36a6372c00206
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802678"
---
### <a name="aspnet-incorrect-multipart-handling-may-result-in-lost-form-data"></a><span data-ttu-id="96f65-101">ASP.NET 無法正確進行多部分處理，可能會導致遺失表單資料。</span><span class="sxs-lookup"><span data-stu-id="96f65-101">ASP.NET Incorrect multipart handling may result in lost form data.</span></span>

|   |   |
|---|---|
|<span data-ttu-id="96f65-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="96f65-102">Details</span></span>|<span data-ttu-id="96f65-103">在目標為 .NET Framework 4.7.2 和更早版本的應用程式中，ASP.Net 可能無法正確剖析多部分界限值，而導致要求執行期間無法使用表單資料。</span><span class="sxs-lookup"><span data-stu-id="96f65-103">In applications that target .NET Framework 4.7.2 and earlier versions, ASP.Net might incorrectly parse multipart boundary values, resulting in form data being unavailable during request execution.</span></span> <span data-ttu-id="96f65-104">以 .NET Framework 4.8 或更新版本為目標的應用程式則可正確剖析多部分資料，因此在要求執行期間可使用表單值。</span><span class="sxs-lookup"><span data-stu-id="96f65-104">Applications that target .NET Framework 4.8 or later versions correctly parse multipart data, so form values are available during request execution.</span></span>|
|<span data-ttu-id="96f65-105">建議</span><span class="sxs-lookup"><span data-stu-id="96f65-105">Suggestion</span></span>|<span data-ttu-id="96f65-106">從執行 .NET Framework 4.8 的應用程式開始，當使用 <code>targetFrameworkVersion</code> 項目將目標設為 .NET Framework 4.8 或更新版本時，預設行為會變更為去除分隔符號。</span><span class="sxs-lookup"><span data-stu-id="96f65-106">Starting with applications running on .NET Framework 4.8, when targeting .NET Framework 4.8 or later by using the <code>targetFrameworkVersion</code> element, the default behavior changes to strip delimiters.</span></span> <span data-ttu-id="96f65-107">當以舊版 Framework 為目標，或不使用 <code>targetFrameworkVersion</code> 時，仍會傳回某些值的尾端分隔符號。您也可以使用 <code>appSetting</code> 明確地控制此行為：</span><span class="sxs-lookup"><span data-stu-id="96f65-107">When targeting previous framework versions or not using <code>targetFrameworkVersion</code>, trailing delimiters for some values are still returned.This behavior can also be explicitly controlled with an <code>appSetting</code>:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:UseLegacyMultiValueHeaderHandling&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="96f65-108">範圍</span><span class="sxs-lookup"><span data-stu-id="96f65-108">Scope</span></span>|<span data-ttu-id="96f65-109">不明</span><span class="sxs-lookup"><span data-stu-id="96f65-109">Unknown</span></span>|
|<span data-ttu-id="96f65-110">版本</span><span class="sxs-lookup"><span data-stu-id="96f65-110">Version</span></span>|<span data-ttu-id="96f65-111">4.8</span><span class="sxs-lookup"><span data-stu-id="96f65-111">4.8</span></span>|
|<span data-ttu-id="96f65-112">類型</span><span class="sxs-lookup"><span data-stu-id="96f65-112">Type</span></span>|<span data-ttu-id="96f65-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="96f65-113">Runtime</span></span>|
|<span data-ttu-id="96f65-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="96f65-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRequest.Form?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.Files?displayProperty=nameWithType></li><li><xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|

