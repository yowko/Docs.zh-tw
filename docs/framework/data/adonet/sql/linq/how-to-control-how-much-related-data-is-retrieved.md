---
title: 如何：控制擷取的相關資料多寡
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 202e33f3130e8db7269af2b4669690cf5c6468cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360853"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="bbbec-102">如何：控制擷取的相關資料多寡</span><span class="sxs-lookup"><span data-stu-id="bbbec-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="bbbec-103">使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 方法可指定與您主要目標有關、應該同時擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="bbbec-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="bbbec-104">例如，如果您預先得知需要客戶訂單的相關資訊，則可以使用 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>，以確保在擷取客戶資訊的同時也會擷取訂單資訊。</span><span class="sxs-lookup"><span data-stu-id="bbbec-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="bbbec-105">這種方法只要存取一次資料庫，就可以同時取得兩個資訊集。</span><span class="sxs-lookup"><span data-stu-id="bbbec-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbbec-106">您可以將叉積擷取為一個大型投影 (如在找到客戶時擷取訂單)，以擷取與查詢之主要目標相關的資料。</span><span class="sxs-lookup"><span data-stu-id="bbbec-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="bbbec-107">但是這種方法通常有其缺點。</span><span class="sxs-lookup"><span data-stu-id="bbbec-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="bbbec-108">例如，其結果只是投影，而不是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可以變更和持續 (Persist) 的實體 (Entity)。</span><span class="sxs-lookup"><span data-stu-id="bbbec-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="bbbec-109">而且您可能會擷取到很多不需要的資料。</span><span class="sxs-lookup"><span data-stu-id="bbbec-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbbec-110">範例</span><span class="sxs-lookup"><span data-stu-id="bbbec-110">Example</span></span>  
 <span data-ttu-id="bbbec-111">在下列範例中，執行查詢時，會擷取位在倫敦 (London) 之所有 `Orders` 的所有 `Customers`。</span><span class="sxs-lookup"><span data-stu-id="bbbec-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="bbbec-112">如此一來，後續存取 `Orders` 物件上的 `Customer` 屬性時，便不會觸發新的資料庫查詢。</span><span class="sxs-lookup"><span data-stu-id="bbbec-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bbbec-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbbec-113">See Also</span></span>  
 [<span data-ttu-id="bbbec-114">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="bbbec-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
