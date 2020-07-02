---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619959"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="5712b-101">還原序列化跨應用程式網域的物件會失敗</span><span class="sxs-lookup"><span data-stu-id="5712b-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="5712b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5712b-102">Details</span></span>

<span data-ttu-id="5712b-103">在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式網域時，嘗試在邏輯呼叫內容中還原序列化跨應用程式網域的物件會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5712b-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5712b-104">建議</span><span class="sxs-lookup"><span data-stu-id="5712b-104">Suggestion</span></span>

<span data-ttu-id="5712b-105">請參閱[緩和：在應用程式定義域之間還原序列化物件](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="5712b-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="5712b-106">名稱</span><span class="sxs-lookup"><span data-stu-id="5712b-106">Name</span></span>    | <span data-ttu-id="5712b-107">值</span><span class="sxs-lookup"><span data-stu-id="5712b-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5712b-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="5712b-108">Scope</span></span>   |<span data-ttu-id="5712b-109">Edge</span><span class="sxs-lookup"><span data-stu-id="5712b-109">Edge</span></span>|
|<span data-ttu-id="5712b-110">版本</span><span class="sxs-lookup"><span data-stu-id="5712b-110">Version</span></span>|<span data-ttu-id="5712b-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="5712b-111">4.5.1</span></span>|
|<span data-ttu-id="5712b-112">類型</span><span class="sxs-lookup"><span data-stu-id="5712b-112">Type</span></span>|<span data-ttu-id="5712b-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="5712b-113">Runtime</span></span>|
