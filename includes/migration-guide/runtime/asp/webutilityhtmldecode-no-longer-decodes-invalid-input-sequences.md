---
ms.openlocfilehash: 0b7d6d9543035ab0a8fdda675ae71572ace12a1f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619934"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="e80c6-101">WebUtility.HtmlDecode 不再將無效的輸入序列解碼</span><span class="sxs-lookup"><span data-stu-id="e80c6-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

#### <a name="details"></a><span data-ttu-id="e80c6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e80c6-102">Details</span></span>

<span data-ttu-id="e80c6-103">根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串，</span><span class="sxs-lookup"><span data-stu-id="e80c6-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="e80c6-104">而是改為傳回原始輸入。</span><span class="sxs-lookup"><span data-stu-id="e80c6-104">Instead, they return the original input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e80c6-105">建議</span><span class="sxs-lookup"><span data-stu-id="e80c6-105">Suggestion</span></span>

<span data-ttu-id="e80c6-106">解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。</span><span class="sxs-lookup"><span data-stu-id="e80c6-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="e80c6-107">若要明確控制這個行為，請將 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) 項目的 <code>aspnet:AllowRelaxedUnicodeDecoding</code> 屬性設為 <code>true</code> 以啟用舊版行為，或是設為 <code>false</code> 以啟用目前的行為。</span><span class="sxs-lookup"><span data-stu-id="e80c6-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>

| <span data-ttu-id="e80c6-108">名稱</span><span class="sxs-lookup"><span data-stu-id="e80c6-108">Name</span></span>    | <span data-ttu-id="e80c6-109">值</span><span class="sxs-lookup"><span data-stu-id="e80c6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e80c6-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="e80c6-110">Scope</span></span>   |<span data-ttu-id="e80c6-111">Minor</span><span class="sxs-lookup"><span data-stu-id="e80c6-111">Minor</span></span>|
|<span data-ttu-id="e80c6-112">版本</span><span class="sxs-lookup"><span data-stu-id="e80c6-112">Version</span></span>|<span data-ttu-id="e80c6-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e80c6-113">4.5</span></span>|
|<span data-ttu-id="e80c6-114">類型</span><span class="sxs-lookup"><span data-stu-id="e80c6-114">Type</span></span>|<span data-ttu-id="e80c6-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="e80c6-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e80c6-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e80c6-116">Affected APIs</span></span>

-<xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
