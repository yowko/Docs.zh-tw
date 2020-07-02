---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620006"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="31155-101">Sql_variant 資料使用的是 sql_variant 定序，而不是資料庫定序</span><span class="sxs-lookup"><span data-stu-id="31155-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="31155-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="31155-102">Details</span></span>

<span data-ttu-id="31155-103"><code>sql_variant</code> 資料使用的是 <code>sql_variant</code> 定序，而不是資料庫定序。</span><span class="sxs-lookup"><span data-stu-id="31155-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="31155-104">建議</span><span class="sxs-lookup"><span data-stu-id="31155-104">Suggestion</span></span>

<span data-ttu-id="31155-105">這項變更可以解決資料庫定序與 <code>sql_variant</code> 定序不同時，可能發生的資料毀損。</span><span class="sxs-lookup"><span data-stu-id="31155-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="31155-106">依賴損毀資料的應用程式可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="31155-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="31155-107">名稱</span><span class="sxs-lookup"><span data-stu-id="31155-107">Name</span></span>    | <span data-ttu-id="31155-108">值</span><span class="sxs-lookup"><span data-stu-id="31155-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="31155-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="31155-109">Scope</span></span>   |<span data-ttu-id="31155-110">透明</span><span class="sxs-lookup"><span data-stu-id="31155-110">Transparent</span></span>|
|<span data-ttu-id="31155-111">版本</span><span class="sxs-lookup"><span data-stu-id="31155-111">Version</span></span>|<span data-ttu-id="31155-112">4.5</span><span class="sxs-lookup"><span data-stu-id="31155-112">4.5</span></span>|
|<span data-ttu-id="31155-113">類型</span><span class="sxs-lookup"><span data-stu-id="31155-113">Type</span></span>|<span data-ttu-id="31155-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="31155-114">Runtime</span></span>|
