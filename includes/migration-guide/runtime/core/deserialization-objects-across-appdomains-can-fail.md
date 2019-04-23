---
ms.openlocfilehash: 891c29b731214fb0028e960256b79cfc267d86b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803469"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="caffc-101">還原序列化跨應用程式網域的物件會失敗</span><span class="sxs-lookup"><span data-stu-id="caffc-101">Deserialization of objects across appdomains can fail</span></span>

|   |   |
|---|---|
|<span data-ttu-id="caffc-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="caffc-102">Details</span></span>|<span data-ttu-id="caffc-103">在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式網域時，嘗試在邏輯呼叫內容中還原序列化跨應用程式網域的物件會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="caffc-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>|
|<span data-ttu-id="caffc-104">建議</span><span class="sxs-lookup"><span data-stu-id="caffc-104">Suggestion</span></span>|<span data-ttu-id="caffc-105">請參閱[風險降低：在應用程式定義域之間將物件還原序列化](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="caffc-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>|
|<span data-ttu-id="caffc-106">範圍</span><span class="sxs-lookup"><span data-stu-id="caffc-106">Scope</span></span>|<span data-ttu-id="caffc-107">Edge</span><span class="sxs-lookup"><span data-stu-id="caffc-107">Edge</span></span>|
|<span data-ttu-id="caffc-108">版本</span><span class="sxs-lookup"><span data-stu-id="caffc-108">Version</span></span>|<span data-ttu-id="caffc-109">4.5.1</span><span class="sxs-lookup"><span data-stu-id="caffc-109">4.5.1</span></span>|
|<span data-ttu-id="caffc-110">類型</span><span class="sxs-lookup"><span data-stu-id="caffc-110">Type</span></span>|<span data-ttu-id="caffc-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="caffc-111">Runtime</span></span>|
