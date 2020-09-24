---
title: 繼承支援
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 7673e69458d5c1af854747c43ba463332a9cd588
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158249"
---
# <a name="inheritance-support"></a><span data-ttu-id="f311a-102">繼承支援</span><span class="sxs-lookup"><span data-stu-id="f311a-102">Inheritance Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="f311a-103">支援 *單一資料表對應*。</span><span class="sxs-lookup"><span data-stu-id="f311a-103">supports *single-table mapping*.</span></span> <span data-ttu-id="f311a-104">換句話說，完整的繼承階層架構 (Inheritance Hierarchy) 會儲存在單一資料庫資料表中。</span><span class="sxs-lookup"><span data-stu-id="f311a-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="f311a-105">這張資料表包含整個階層架構中所有可能之資料行的平面聯集 </span><span class="sxs-lookup"><span data-stu-id="f311a-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="f311a-106"> (等位是將兩個數據表結合成一個資料表的結果，而該資料表具有存在於原始資料表中的資料列 ) 。在資料行中，每個資料列都有 null，而這些資料行不會套用至資料列所代表之實例的類型。</span><span class="sxs-lookup"><span data-stu-id="f311a-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="f311a-107">單一資料表對應策略是最簡單的繼承表示，並且可以在許多不同類別的查詢中提供良好的效能特性。</span><span class="sxs-lookup"><span data-stu-id="f311a-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="f311a-108">若要在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中實作這個對應，則必須在繼承階層架構的根類別中指定屬性 (Attribute) 和屬性的屬性 (Attribute Property)。</span><span class="sxs-lookup"><span data-stu-id="f311a-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="f311a-109">如需詳細資訊，請參閱 [如何：對應繼承](how-to-map-inheritance-hierarchies.md)階層架構。</span><span class="sxs-lookup"><span data-stu-id="f311a-109">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="f311a-110">使用 Visual Studio 的開發人員也可以使用物件關聯式設計工具來對應繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="f311a-110">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f311a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f311a-111">See also</span></span>

- [<span data-ttu-id="f311a-112">背景資訊</span><span class="sxs-lookup"><span data-stu-id="f311a-112">Background Information</span></span>](background-information.md)
