---
ms.openlocfilehash: ef3114a4eb9f62030c3ec36d3b463d07ccd59f6d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496364"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="d17c1-101">WebUtility.HtmlDecode 不再將無效的輸入序列解碼</span><span class="sxs-lookup"><span data-stu-id="d17c1-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

#### <a name="details"></a><span data-ttu-id="d17c1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d17c1-102">Details</span></span>

<span data-ttu-id="d17c1-103">根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串，</span><span class="sxs-lookup"><span data-stu-id="d17c1-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="d17c1-104">而是改為傳回原始輸入。</span><span class="sxs-lookup"><span data-stu-id="d17c1-104">Instead, they return the original input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d17c1-105">建議</span><span class="sxs-lookup"><span data-stu-id="d17c1-105">Suggestion</span></span>

<span data-ttu-id="d17c1-106">解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。</span><span class="sxs-lookup"><span data-stu-id="d17c1-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="d17c1-107">若要明確控制這個行為，請將 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) 項目的 <code>aspnet:AllowRelaxedUnicodeDecoding</code> 屬性設為 <code>true</code> 以啟用舊版行為，或是設為 <code>false</code> 以啟用目前的行為。</span><span class="sxs-lookup"><span data-stu-id="d17c1-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>

| <span data-ttu-id="d17c1-108">名稱</span><span class="sxs-lookup"><span data-stu-id="d17c1-108">Name</span></span>    | <span data-ttu-id="d17c1-109">值</span><span class="sxs-lookup"><span data-stu-id="d17c1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d17c1-110">範圍</span><span class="sxs-lookup"><span data-stu-id="d17c1-110">Scope</span></span>   |<span data-ttu-id="d17c1-111">Minor</span><span class="sxs-lookup"><span data-stu-id="d17c1-111">Minor</span></span>|
|<span data-ttu-id="d17c1-112">版本</span><span class="sxs-lookup"><span data-stu-id="d17c1-112">Version</span></span>|<span data-ttu-id="d17c1-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d17c1-113">4.5</span></span>|
|<span data-ttu-id="d17c1-114">類型</span><span class="sxs-lookup"><span data-stu-id="d17c1-114">Type</span></span>|<span data-ttu-id="d17c1-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="d17c1-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d17c1-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="d17c1-116">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.WebUtility.HtmlDecode(System.String)`
- `M:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)`
- `M:System.Net.WebUtility.UrlDecode(System.String)`

-->
