---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616037"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="8c89b-101">DbParameter.Precision 和 DbParameter.Scale 現在是公用虛擬成員</span><span class="sxs-lookup"><span data-stu-id="8c89b-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

#### <a name="details"></a><span data-ttu-id="8c89b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8c89b-102">Details</span></span>

<span data-ttu-id="8c89b-103"><xref:System.Data.Common.DbParameter.Precision> 和 <xref:System.Data.Common.DbParameter.Scale> 會當做公用虛擬屬性來實作。</span><span class="sxs-lookup"><span data-stu-id="8c89b-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="8c89b-104">這些屬性取代對應的明確介面實作 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> 和 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>。</span><span class="sxs-lookup"><span data-stu-id="8c89b-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8c89b-105">建議</span><span class="sxs-lookup"><span data-stu-id="8c89b-105">Suggestion</span></span>

<span data-ttu-id="8c89b-106">重建 ADO.NET 資料庫提供者時，這些差異會要求將 'override' 關鍵字套用至 Precision 和 Scale 屬性。</span><span class="sxs-lookup"><span data-stu-id="8c89b-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="8c89b-107">只有在重建元件時才需要這樣做；現有的二進位檔將繼續運作。</span><span class="sxs-lookup"><span data-stu-id="8c89b-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>

| <span data-ttu-id="8c89b-108">名稱</span><span class="sxs-lookup"><span data-stu-id="8c89b-108">Name</span></span>    | <span data-ttu-id="8c89b-109">值</span><span class="sxs-lookup"><span data-stu-id="8c89b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8c89b-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8c89b-110">Scope</span></span>   | <span data-ttu-id="8c89b-111">Minor</span><span class="sxs-lookup"><span data-stu-id="8c89b-111">Minor</span></span>       |
| <span data-ttu-id="8c89b-112">版本</span><span class="sxs-lookup"><span data-stu-id="8c89b-112">Version</span></span> | <span data-ttu-id="8c89b-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="8c89b-113">4.5.1</span></span>       |
| <span data-ttu-id="8c89b-114">類型</span><span class="sxs-lookup"><span data-stu-id="8c89b-114">Type</span></span>    | <span data-ttu-id="8c89b-115">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8c89b-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8c89b-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8c89b-116">Affected APIs</span></span>

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
