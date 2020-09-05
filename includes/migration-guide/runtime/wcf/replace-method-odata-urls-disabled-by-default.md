---
ms.openlocfilehash: fccf349517133245ec85ae3c25cedbfb27a7dd8b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496988"
---
### <a name="the-replace-method-in-odata-urls-is-disabled-by-default"></a><span data-ttu-id="3d095-101">OData URL 中的 Replace 方法預設為停用</span><span class="sxs-lookup"><span data-stu-id="3d095-101">The Replace method in OData URLs is disabled by default</span></span>

#### <a name="details"></a><span data-ttu-id="3d095-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3d095-102">Details</span></span>

<span data-ttu-id="3d095-103">從 .NET Framework 4.5 開始，OData URL 中的 Replace 方法預設為停用。</span><span class="sxs-lookup"><span data-stu-id="3d095-103">Beginning in the .NET Framework 4.5, the Replace method in OData URLs is disabled by default.</span></span> <span data-ttu-id="3d095-104">當 OData Replace 停用 (現在為預設) 時，任何包含取代功能的使用者要求 (不常見) 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3d095-104">When OData Replace is disabled (now by default), any user requests including replace functions (which are uncommon) will fail.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3d095-105">建議</span><span class="sxs-lookup"><span data-stu-id="3d095-105">Suggestion</span></span>

<span data-ttu-id="3d095-106">如果需要 Replace 方法 (不常見)，可以透過組態設定 (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>) 將它重新啟用。</span><span class="sxs-lookup"><span data-stu-id="3d095-106">If the replace method is required (which is uncommon), it can be re-enabled through a config settings (<xref:System.Data.Services.Configuration.DataServicesFeaturesSection.ReplaceFunction?displayProperty=fullName>).</span></span> <span data-ttu-id="3d095-107">不過，已啟用的 Replace 方法可能會有資訊安全漏洞，因此只有在仔細檢閱之後才能使用。</span><span class="sxs-lookup"><span data-stu-id="3d095-107">However, an enabled replace method can open security vulnerabilities and should only be used after careful review.</span></span>

| <span data-ttu-id="3d095-108">名稱</span><span class="sxs-lookup"><span data-stu-id="3d095-108">Name</span></span>    | <span data-ttu-id="3d095-109">值</span><span class="sxs-lookup"><span data-stu-id="3d095-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3d095-110">範圍</span><span class="sxs-lookup"><span data-stu-id="3d095-110">Scope</span></span>   |<span data-ttu-id="3d095-111">Edge</span><span class="sxs-lookup"><span data-stu-id="3d095-111">Edge</span></span>|
|<span data-ttu-id="3d095-112">版本</span><span class="sxs-lookup"><span data-stu-id="3d095-112">Version</span></span>|<span data-ttu-id="3d095-113">4.5</span><span class="sxs-lookup"><span data-stu-id="3d095-113">4.5</span></span>|
|<span data-ttu-id="3d095-114">類型</span><span class="sxs-lookup"><span data-stu-id="3d095-114">Type</span></span>|<span data-ttu-id="3d095-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="3d095-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3d095-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3d095-116">Affected APIs</span></span>

- <xref:System.Data.Services.DataService%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``T:System.Data.Services.DataService`1``

-->
