---
ms.openlocfilehash: 6dc3669433804a4524c18d5a932f9879343ab508
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235128"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="877be-101">OData URL 中的 Replace 方法預設為停用</span><span class="sxs-lookup"><span data-stu-id="877be-101">The Replace method in OData URLs is disabled by default</span></span>

|   |   |
|---|---|
|<span data-ttu-id="877be-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="877be-102">Details</span></span>|<span data-ttu-id="877be-103">從 .NET Framework 4.5 開始，OData URL 中的 Replace 方法預設為停用。</span><span class="sxs-lookup"><span data-stu-id="877be-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="877be-104">當 OData Replace 停用 (現在為預設) 時，任何包含取代功能的使用者要求 (不常見) 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="877be-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>|
|<span data-ttu-id="877be-105">建議</span><span class="sxs-lookup"><span data-stu-id="877be-105">Suggestion</span></span>|<span data-ttu-id="877be-106">如果需要 Replace 方法 (不常見)，可以透過組態設定 (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>) 將它重新啟用。</span><span class="sxs-lookup"><span data-stu-id="877be-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=name>).</span></span> <span data-ttu-id="877be-107">不過，已啟用的 Replace 方法可能會有資訊安全漏洞，因此只有在仔細檢閱之後才能使用。</span><span class="sxs-lookup"><span data-stu-id="877be-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>|
|<span data-ttu-id="877be-108">範圍</span><span class="sxs-lookup"><span data-stu-id="877be-108">Scope</span></span>|<span data-ttu-id="877be-109">Edge</span><span class="sxs-lookup"><span data-stu-id="877be-109">Edge</span></span>|
|<span data-ttu-id="877be-110">版本</span><span class="sxs-lookup"><span data-stu-id="877be-110">Version</span></span>|<span data-ttu-id="877be-111">4.5</span><span class="sxs-lookup"><span data-stu-id="877be-111">4.5</span></span>|
|<span data-ttu-id="877be-112">類型</span><span class="sxs-lookup"><span data-stu-id="877be-112">Type</span></span>|<span data-ttu-id="877be-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="877be-113">Runtime</span></span>|
|<span data-ttu-id="877be-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="877be-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Services.DataService%601?displayProperty=nameWithType></li></ul>|
