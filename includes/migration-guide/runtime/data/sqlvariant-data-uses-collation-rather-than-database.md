---
ms.openlocfilehash: fb339fb35cdcbba4f1c860fae9c17162c4cff596
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497429"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="b26e0-101">Sql_variant 資料使用的是 sql_variant 定序，而不是資料庫定序</span><span class="sxs-lookup"><span data-stu-id="b26e0-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="b26e0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b26e0-102">Details</span></span>

<span data-ttu-id="b26e0-103"><code>sql_variant</code> 資料使用的是 <code>sql_variant</code> 定序，而不是資料庫定序。</span><span class="sxs-lookup"><span data-stu-id="b26e0-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b26e0-104">建議</span><span class="sxs-lookup"><span data-stu-id="b26e0-104">Suggestion</span></span>

<span data-ttu-id="b26e0-105">這項變更可以解決資料庫定序與 <code>sql_variant</code> 定序不同時，可能發生的資料毀損。</span><span class="sxs-lookup"><span data-stu-id="b26e0-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="b26e0-106">依賴損毀資料的應用程式可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="b26e0-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="b26e0-107">名稱</span><span class="sxs-lookup"><span data-stu-id="b26e0-107">Name</span></span>    | <span data-ttu-id="b26e0-108">值</span><span class="sxs-lookup"><span data-stu-id="b26e0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b26e0-109">範圍</span><span class="sxs-lookup"><span data-stu-id="b26e0-109">Scope</span></span>   |<span data-ttu-id="b26e0-110">透明</span><span class="sxs-lookup"><span data-stu-id="b26e0-110">Transparent</span></span>|
|<span data-ttu-id="b26e0-111">版本</span><span class="sxs-lookup"><span data-stu-id="b26e0-111">Version</span></span>|<span data-ttu-id="b26e0-112">4.5</span><span class="sxs-lookup"><span data-stu-id="b26e0-112">4.5</span></span>|
|<span data-ttu-id="b26e0-113">類型</span><span class="sxs-lookup"><span data-stu-id="b26e0-113">Type</span></span>|<span data-ttu-id="b26e0-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="b26e0-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b26e0-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b26e0-115">Affected APIs</span></span>

<span data-ttu-id="b26e0-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="b26e0-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
