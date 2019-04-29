---
title: 查詢結果
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: 70aa2ad6385ec4791b05b202dc5dc6d4fe9e57b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797835"
---
# <a name="query-results"></a><span data-ttu-id="2bece-102">查詢結果</span><span class="sxs-lookup"><span data-stu-id="2bece-102">Query Results</span></span>
<span data-ttu-id="2bece-103">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢轉換成命令樹並且執行之後，查詢結果通常會傳回成為下列其中一種形式：</span><span class="sxs-lookup"><span data-stu-id="2bece-103">After a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is converted to command trees and executed, the query results are usually returned as one of the following:</span></span>  
  
- <span data-ttu-id="2bece-104">零個或多個具型別實體物件的集合，或是概念模型中複雜類型的投影。</span><span class="sxs-lookup"><span data-stu-id="2bece-104">A collection of zero or more typed entity objects or a projection of complex types in the conceptual model.</span></span>  
  
- <span data-ttu-id="2bece-105">概念模型支援的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="2bece-105">CLR types supported by the conceptual model.</span></span>  
  
- <span data-ttu-id="2bece-106">內嵌集合。</span><span class="sxs-lookup"><span data-stu-id="2bece-106">Inline collections.</span></span>  
  
- <span data-ttu-id="2bece-107">匿名型別。</span><span class="sxs-lookup"><span data-stu-id="2bece-107">Anonymous types.</span></span>  
  
 <span data-ttu-id="2bece-108">針對資料來源執行查詢之後，便會將結果具體化成為 CLR 型別，然後傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="2bece-108">When the query has executed against the data source, the results are materialized into CLR types and returned to the client.</span></span> <span data-ttu-id="2bece-109">所有物件具體化都是由 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 執行。</span><span class="sxs-lookup"><span data-stu-id="2bece-109">All object materialization is performed by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="2bece-110">因為無法在 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 與 CLR 之間對應而產生的任何錯誤，都將導致物件具體化期間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2bece-110">Any errors that result from an inability to map between the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] and the CLR will cause exceptions to be thrown during object materialization.</span></span>  
  
 <span data-ttu-id="2bece-111">如果查詢執行傳回基本概念模型型別，結果將由獨立且從 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 中斷連接的 CLR 型別構成。</span><span class="sxs-lookup"><span data-stu-id="2bece-111">If the query execution returns primitive conceptual model types, the results consist of CLR types that are stand-alone and disconnected from the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="2bece-112">但是，如果查詢傳回以 <xref:System.Data.Objects.ObjectQuery%601> 表示的具型別實體物件集合，這些型別將會由此內容物件追蹤。</span><span class="sxs-lookup"><span data-stu-id="2bece-112">However, if the query returns a collection of typed entity objects, represented by <xref:System.Data.Objects.ObjectQuery%601>, those types are tracked by the object context.</span></span> <span data-ttu-id="2bece-113">（例如子/父集合、 變更追蹤、 多型，等等） 的所有物件行為都會如同[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2bece-113">All object behavior (such as child/parent collections, change tracking, polymorphism, and so on) are as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="2bece-114">這項功能可以依照 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 中所定義的能力使用。</span><span class="sxs-lookup"><span data-stu-id="2bece-114">This functionality can be used in its capacity, as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="2bece-115">如需詳細資訊，請參閱 <<c0> [ 使用物件](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="2bece-115">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="2bece-116">從查詢傳回的結構型別 (例如匿名型別和可為 null 的複雜類型) 可能是 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="2bece-116">Struct types returned from queries (such as anonymous types and nullable complex types) can be of `null` value.</span></span> <span data-ttu-id="2bece-117">所傳回實體的 <xref:System.Data.Objects.DataClasses.EntityCollection%601> 屬性也可能是 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="2bece-117">An <xref:System.Data.Objects.DataClasses.EntityCollection%601> property of a returned entity can also be of `null` value.</span></span> <span data-ttu-id="2bece-118">投影 `null` 值之實體的屬性集合就可能產生這種情況，例如在沒有項目的 <xref:System.Linq.Queryable.FirstOrDefault%2A> 上呼叫 <xref:System.Data.Objects.ObjectQuery%601>。</span><span class="sxs-lookup"><span data-stu-id="2bece-118">This can result from projecting the collection property of an entity that is of `null` value, such as calling <xref:System.Linq.Queryable.FirstOrDefault%2A> on an <xref:System.Data.Objects.ObjectQuery%601> that has no elements.</span></span>  
  
 <span data-ttu-id="2bece-119">在某些情況下，查詢看起來好像會在執行期間產生具體化結果，但是查詢是要在伺服器上執行，所以實體物件永遠也不會在 CLR 中具體化。</span><span class="sxs-lookup"><span data-stu-id="2bece-119">In certain situations, a query might appear to generate a materialized result during its execution, but the query will be executed on the server and the entity object will never be materialized in the CLR.</span></span> <span data-ttu-id="2bece-120">如果您需要用到物件具體化的副作用，這種情況將會造成問題。</span><span class="sxs-lookup"><span data-stu-id="2bece-120">This can cause problems if you are depending on side effects of object materialization.</span></span>  
  
 <span data-ttu-id="2bece-121">以下範例包含具有 `MyContact` 屬性的自訂類別 `LastName`。</span><span class="sxs-lookup"><span data-stu-id="2bece-121">The following example contains a custom class, `MyContact`, with a `LastName` property.</span></span> <span data-ttu-id="2bece-122">當 `LastName` 屬性設定之後，`count` 變數就會累加。</span><span class="sxs-lookup"><span data-stu-id="2bece-122">When the `LastName` property is set, a `count` variable is incremented.</span></span> <span data-ttu-id="2bece-123">如果您執行以下兩個查詢，第一個查詢會累加 `count`，但第二個查詢則不會。</span><span class="sxs-lookup"><span data-stu-id="2bece-123">If you execute the two following queries, the first query will increment `count` while the second query will not.</span></span> <span data-ttu-id="2bece-124">這是因為在第二個查詢中 `LastName` 屬性是從結果投影的，而且根本沒有建立 `MyContact` 類別，因為在存放區上執行此查詢並不要用到它。</span><span class="sxs-lookup"><span data-stu-id="2bece-124">This is because in the second query the `LastName` property is projected from the results and the `MyContact` class is never created, because it is not required to execute the query on the store.</span></span>  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
