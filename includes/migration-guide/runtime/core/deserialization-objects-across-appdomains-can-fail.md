---
ms.openlocfilehash: 3f82a4daac3b5d8981532f0c82e9a76f13c68b6e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497778"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="620ac-101">還原序列化跨應用程式網域的物件會失敗</span><span class="sxs-lookup"><span data-stu-id="620ac-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="620ac-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="620ac-102">Details</span></span>

<span data-ttu-id="620ac-103">在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式網域時，嘗試在邏輯呼叫內容中還原序列化跨應用程式網域的物件會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="620ac-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="620ac-104">建議</span><span class="sxs-lookup"><span data-stu-id="620ac-104">Suggestion</span></span>

<span data-ttu-id="620ac-105">請參閱[緩和：在應用程式定義域之間還原序列化物件](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="620ac-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="620ac-106">名稱</span><span class="sxs-lookup"><span data-stu-id="620ac-106">Name</span></span>    | <span data-ttu-id="620ac-107">值</span><span class="sxs-lookup"><span data-stu-id="620ac-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="620ac-108">範圍</span><span class="sxs-lookup"><span data-stu-id="620ac-108">Scope</span></span>   |<span data-ttu-id="620ac-109">Edge</span><span class="sxs-lookup"><span data-stu-id="620ac-109">Edge</span></span>|
|<span data-ttu-id="620ac-110">版本</span><span class="sxs-lookup"><span data-stu-id="620ac-110">Version</span></span>|<span data-ttu-id="620ac-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="620ac-111">4.5.1</span></span>|
|<span data-ttu-id="620ac-112">類型</span><span class="sxs-lookup"><span data-stu-id="620ac-112">Type</span></span>|<span data-ttu-id="620ac-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="620ac-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="620ac-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="620ac-114">Affected APIs</span></span>

<span data-ttu-id="620ac-115">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="620ac-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
