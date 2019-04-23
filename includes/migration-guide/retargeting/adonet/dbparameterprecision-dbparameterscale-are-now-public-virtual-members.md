---
ms.openlocfilehash: 1721d32f8cdc9b6ea4b4732e38afa56a8a532600
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234653"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="3d911-101">DbParameter.Precision 和 DbParameter.Scale 現在是公用虛擬成員</span><span class="sxs-lookup"><span data-stu-id="3d911-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3d911-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3d911-102">Details</span></span>|<xref:System.Data.Common.DbParameter.Precision> <span data-ttu-id="3d911-103">和 <xref:System.Data.Common.DbParameter.Scale> 會當做公用虛擬屬性來實作。</span><span class="sxs-lookup"><span data-stu-id="3d911-103">and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="3d911-104">這些屬性取代對應的明確介面實作 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> 和 <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>。</span><span class="sxs-lookup"><span data-stu-id="3d911-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>|
|<span data-ttu-id="3d911-105">建議</span><span class="sxs-lookup"><span data-stu-id="3d911-105">Suggestion</span></span>|<span data-ttu-id="3d911-106">重建 ADO.NET 資料庫提供者時，這些差異會要求將 'override' 關鍵字套用至 Precision 和 Scale 屬性。</span><span class="sxs-lookup"><span data-stu-id="3d911-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="3d911-107">只有在重建元件時才需要這樣做；現有的二進位檔將繼續運作。</span><span class="sxs-lookup"><span data-stu-id="3d911-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>|
|<span data-ttu-id="3d911-108">範圍</span><span class="sxs-lookup"><span data-stu-id="3d911-108">Scope</span></span>|<span data-ttu-id="3d911-109">次要</span><span class="sxs-lookup"><span data-stu-id="3d911-109">Minor</span></span>|
|<span data-ttu-id="3d911-110">版本</span><span class="sxs-lookup"><span data-stu-id="3d911-110">Version</span></span>|<span data-ttu-id="3d911-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="3d911-111">4.5.1</span></span>|
|<span data-ttu-id="3d911-112">類型</span><span class="sxs-lookup"><span data-stu-id="3d911-112">Type</span></span>|<span data-ttu-id="3d911-113">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="3d911-113">Retargeting</span></span>|
|<span data-ttu-id="3d911-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3d911-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|
