---
title: 繼承支援
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 668f4f1dd284550e644ce6b8a4491ca47105575e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230911"
---
# <a name="inheritance-support"></a><span data-ttu-id="5da3a-102">繼承支援</span><span class="sxs-lookup"><span data-stu-id="5da3a-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5da3a-103">支援*單一資料表對應*。</span><span class="sxs-lookup"><span data-stu-id="5da3a-103">supports *single-table mapping*.</span></span> <span data-ttu-id="5da3a-104">換句話說，完整的繼承階層架構 (Inheritance Hierarchy) 會儲存在單一資料庫資料表中。</span><span class="sxs-lookup"><span data-stu-id="5da3a-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="5da3a-105">這張資料表包含整個階層架構中所有可能之資料行的平面聯集 </span><span class="sxs-lookup"><span data-stu-id="5da3a-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="5da3a-106">(聯集是指將兩張原始資料表中的資料列集結，並去除重複資料列後所得到的單一資料表結果)。如果資料行不適用於資料列所代表之執行個體的型別，則該資料列中的該資料行會是 null。</span><span class="sxs-lookup"><span data-stu-id="5da3a-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="5da3a-107">單一資料表對應策略是最簡單的繼承表示，並且可以在許多不同類別的查詢中提供良好的效能特性。</span><span class="sxs-lookup"><span data-stu-id="5da3a-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="5da3a-108">若要在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中實作這個對應，則必須在繼承階層架構的根類別中指定屬性 (Attribute) 和屬性的屬性 (Attribute Property)。</span><span class="sxs-lookup"><span data-stu-id="5da3a-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="5da3a-109">如需詳細資訊，請參閱[如何：對應繼承階層架構](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)。</span><span class="sxs-lookup"><span data-stu-id="5da3a-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="5da3a-110">使用 Visual Studio 的開發人員也可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]來對應繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="5da3a-110">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da3a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5da3a-111">See also</span></span>

- [<span data-ttu-id="5da3a-112">背景資訊</span><span class="sxs-lookup"><span data-stu-id="5da3a-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
