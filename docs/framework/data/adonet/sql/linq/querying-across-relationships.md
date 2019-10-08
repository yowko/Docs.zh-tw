---
title: 跨關聯性查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: 1675e4c6a610373e1c981b383ae0229739d96dd0
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003325"
---
# <a name="querying-across-relationships"></a><span data-ttu-id="0cb05-102">跨關聯性查詢</span><span class="sxs-lookup"><span data-stu-id="0cb05-102">Querying Across Relationships</span></span>
<span data-ttu-id="0cb05-103">對類別定義中其他物件或其他物件集合的參考，會直接對應到資料庫中的外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="0cb05-103">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="0cb05-104">您可以在使用點標記法進行查詢時使用這些關聯性，進而存取關聯性屬性以及從某個物件巡覽到另一個物件。</span><span class="sxs-lookup"><span data-stu-id="0cb05-104">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="0cb05-105">這些存取作業會轉譯成對等 SQL 中更複雜的聯結或相關聯的子查詢 (Subquery)。</span><span class="sxs-lookup"><span data-stu-id="0cb05-105">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="0cb05-106">例如，下列查詢會從訂單巡覽至客戶，而將查詢結果限制在位於倫敦 (London) 之客戶的訂單。</span><span class="sxs-lookup"><span data-stu-id="0cb05-106">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="0cb05-107">如果關聯性屬性不存在，您必須以手動方式將它們撰寫為*聯結，如同*在 SQL 查詢中所做的一樣，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="0cb05-107">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="0cb05-108">您可以使用*relationship*屬性，一次定義此特定關聯性。</span><span class="sxs-lookup"><span data-stu-id="0cb05-108">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="0cb05-109">然後，您就可以使用更為方便的點語法。</span><span class="sxs-lookup"><span data-stu-id="0cb05-109">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="0cb05-110">但是關聯性屬性的存在更加重要，因為網域指定的物件模型 (Object Model) 通常會定義為階層架構或圖形。</span><span class="sxs-lookup"><span data-stu-id="0cb05-110">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="0cb05-111">您進行程式設計的物件會具有對其他物件的參考。</span><span class="sxs-lookup"><span data-stu-id="0cb05-111">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="0cb05-112">物件對物件的關聯性會對應到資料庫中的外部索引鍵樣式關聯性，只是純屬巧合。</span><span class="sxs-lookup"><span data-stu-id="0cb05-112">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="0cb05-113">屬性存取則提供了撰寫聯結的簡便方法。</span><span class="sxs-lookup"><span data-stu-id="0cb05-113">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="0cb05-114">關於這點，相較於成為查詢本身的一部分，關聯性屬性對於查詢的結果而言更加重要。</span><span class="sxs-lookup"><span data-stu-id="0cb05-114">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="0cb05-115">在查詢已擷取特定客戶的相關資料後，類別定義會表示客戶具有訂單。</span><span class="sxs-lookup"><span data-stu-id="0cb05-115">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="0cb05-116">換句話說，您會預期特定客戶的 `Orders` 屬性成為已填入 (Populate) 該客戶所有訂單的集合。</span><span class="sxs-lookup"><span data-stu-id="0cb05-116">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="0cb05-117">事實上，這就是您透過這種方式定義類別而宣告的合約。</span><span class="sxs-lookup"><span data-stu-id="0cb05-117">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="0cb05-118">即使查詢並未要求訂單，您仍預期會在此看見訂單。</span><span class="sxs-lookup"><span data-stu-id="0cb05-118">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="0cb05-119">您期望物件模型能維持某種假象，那就是資料庫的記憶體中擴充具有立即可用的相關物件。</span><span class="sxs-lookup"><span data-stu-id="0cb05-119">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="0cb05-120">您目前具有關聯性，因此可藉由參考類別中定義的關聯性屬性，進而撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="0cb05-120">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="0cb05-121">這些關聯性參考會對應至資料庫中的外部索引鍵關聯性。</span><span class="sxs-lookup"><span data-stu-id="0cb05-121">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="0cb05-122">使用這些關聯性的作業會轉譯成對等 SQL 中更複雜的聯結。</span><span class="sxs-lookup"><span data-stu-id="0cb05-122">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="0cb05-123">只要您已定義關聯性 (使用 <xref:System.Data.Linq.Mapping.AssociationAttribute> 屬性 (Attribute))，就不必在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中編寫明確聯結。</span><span class="sxs-lookup"><span data-stu-id="0cb05-123">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="0cb05-124">為協助維護這種假像，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會執行一個稱為*延後載入*的技術。</span><span class="sxs-lookup"><span data-stu-id="0cb05-124">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="0cb05-125">如需詳細資訊，請參閱[延後與立即載入](deferred-versus-immediate-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb05-125">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="0cb05-126">請考慮下列 SQL 查詢，以投影 `CustomerID` @ no__t-1 @ no__t-2 配對的清單：</span><span class="sxs-lookup"><span data-stu-id="0cb05-126">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="0cb05-127">若要使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 取得相同的結果，您可使用已存在於 `Orders` 類別中的 `Customer` 屬性參考。</span><span class="sxs-lookup"><span data-stu-id="0cb05-127">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="0cb05-128">@No__t-0 參考提供執行查詢和投影 `CustomerID` @ no__t-2 @ no__t-3 配對的必要資訊，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="0cb05-128">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="0cb05-129">您也可以進行反轉。</span><span class="sxs-lookup"><span data-stu-id="0cb05-129">You can also do the reverse.</span></span> <span data-ttu-id="0cb05-130">也就是說，您可以查詢 `Orders`，並使用其 `Customer` 關聯性參考來存取關聯之 `Customer` 物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0cb05-130">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="0cb05-131">下列程式碼會像之前一樣投射相同的 `CustomerID` @ no__t-1 @ no__t-2 組，但這次是藉由查詢 `Orders` 而不是 `Customers` 來進行。</span><span class="sxs-lookup"><span data-stu-id="0cb05-131">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0cb05-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cb05-132">See also</span></span>

- [<span data-ttu-id="0cb05-133">查詢概念</span><span class="sxs-lookup"><span data-stu-id="0cb05-133">Query Concepts</span></span>](query-concepts.md)
