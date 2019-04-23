---
ms.openlocfilehash: dfc1a0d05142861ff1c1b7391126d86e09fa71c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803544"
---
### <a name="webutilityhtmldecode-no-longer-decodes-invalid-input-sequences"></a><span data-ttu-id="dab52-101">WebUtility.HtmlDecode 不再將無效的輸入序列解碼</span><span class="sxs-lookup"><span data-stu-id="dab52-101">WebUtility.HtmlDecode no longer decodes invalid input sequences</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dab52-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dab52-102">Details</span></span>|<span data-ttu-id="dab52-103">根據預設，解碼方法不再將無效的輸入序列解碼為無效的 UTF-16 字串，</span><span class="sxs-lookup"><span data-stu-id="dab52-103">By default, decoding methods no longer decode an invalid input sequence into an invalid UTF-16 string.</span></span> <span data-ttu-id="dab52-104">而是改為傳回原始輸入。</span><span class="sxs-lookup"><span data-stu-id="dab52-104">Instead, they return the original input.</span></span>|
|<span data-ttu-id="dab52-105">建議</span><span class="sxs-lookup"><span data-stu-id="dab52-105">Suggestion</span></span>|<span data-ttu-id="dab52-106">解碼器輸出的變更只有在您於字串中儲存二進位資料而不是 UTF-16 資料時才相關。</span><span class="sxs-lookup"><span data-stu-id="dab52-106">The change in decoder output should matter only if you store binary data instead of UTF-16 data in strings.</span></span> <span data-ttu-id="dab52-107">若要明確控制這個行為，請將 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) 項目的 <code>aspnet:AllowRelaxedUnicodeDecoding</code> 屬性設為 <code>true</code> 以啟用舊版行為，或是設為 <code>false</code> 以啟用目前的行為。</span><span class="sxs-lookup"><span data-stu-id="dab52-107">To explicitly control this behavior, set the <code>aspnet:AllowRelaxedUnicodeDecoding</code> attribute of the [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/index.md) element to <code>true</code> to enable legacy behavior or to <code>false</code> to enable the current behavior.</span></span>|
|<span data-ttu-id="dab52-108">範圍</span><span class="sxs-lookup"><span data-stu-id="dab52-108">Scope</span></span>|<span data-ttu-id="dab52-109">次要</span><span class="sxs-lookup"><span data-stu-id="dab52-109">Minor</span></span>|
|<span data-ttu-id="dab52-110">版本</span><span class="sxs-lookup"><span data-stu-id="dab52-110">Version</span></span>|<span data-ttu-id="dab52-111">4.5</span><span class="sxs-lookup"><span data-stu-id="dab52-111">4.5</span></span>|
|<span data-ttu-id="dab52-112">類型</span><span class="sxs-lookup"><span data-stu-id="dab52-112">Type</span></span>|<span data-ttu-id="dab52-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="dab52-113">Runtime</span></span>|
|<span data-ttu-id="dab52-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dab52-114">Affected APIs</span></span>|<ul><li><xref:System.Net.WebUtility.HtmlDecode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlDecode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.UrlDecode(System.String)?displayProperty=nameWithType></li></ul>|
