---
title: 從識別快取擷取物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 702d88f844f00b86e64404bd100fd6b3d34971c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211227"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="8c867-102">從識別快取擷取物件</span><span class="sxs-lookup"><span data-stu-id="8c867-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="8c867-103">本主題描述 LINQ to SQL 查詢的類型，這些查詢可從 <xref:System.Data.Linq.DataContext> 所管理的識別快取傳回物件。</span><span class="sxs-lookup"><span data-stu-id="8c867-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="8c867-104">在 LINQ to SQL 中，<xref:System.Data.Linq.DataContext> 用來管理物件的其中一種方式就是在執行查詢時，將物件識別記錄在識別快取中。</span><span class="sxs-lookup"><span data-stu-id="8c867-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="8c867-105">在某些情況下，LINQ to SQL 會先嘗試從識別快取擷取物件，然後再執行資料庫的查詢。</span><span class="sxs-lookup"><span data-stu-id="8c867-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="8c867-106">一般而言，為了讓 LINQ to SQL 查詢從識別快取傳回物件，此查詢必須以物件的主索引鍵為基礎，而且必須傳回單一物件。</span><span class="sxs-lookup"><span data-stu-id="8c867-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="8c867-107">特別是，此查詢必須採用下列其中一種一般格式。</span><span class="sxs-lookup"><span data-stu-id="8c867-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c867-108">預先編譯的查詢不會從識別快取傳回物件。</span><span class="sxs-lookup"><span data-stu-id="8c867-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="8c867-109">如需有關預先編譯的查詢的詳細資訊，請參閱<xref:System.Data.Linq.CompiledQuery>和[How to:儲存並重複使用查詢](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="8c867-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="8c867-110">若要從識別快取擷取物件，查詢必須採用下列其中一種一般格式：</span><span class="sxs-lookup"><span data-stu-id="8c867-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 <span data-ttu-id="8c867-111">在這些一般格式中，`Function1`、`Function2` 和 `predicate` 的定義方式如下。</span><span class="sxs-lookup"><span data-stu-id="8c867-111">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 `Function1` <span data-ttu-id="8c867-112">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="8c867-112">can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` <span data-ttu-id="8c867-113">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="8c867-113">can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` <span data-ttu-id="8c867-114">必須是物件的主索引鍵屬性設為常數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="8c867-114">must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="8c867-115">如果物件具有多個屬性所定義的主索引鍵，每個主索引鍵屬性都必須設定為常數值。</span><span class="sxs-lookup"><span data-stu-id="8c867-115">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="8c867-116">下面是 `predicate` 必須採用的格式範例：</span><span class="sxs-lookup"><span data-stu-id="8c867-116">The following are examples of the form `predicate` must take:</span></span>  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="8c867-117">範例</span><span class="sxs-lookup"><span data-stu-id="8c867-117">Example</span></span>  
 <span data-ttu-id="8c867-118">下列程式碼將提供 LINQ to SQL 查詢類型的範例，這些查詢可從識別快取擷取物件。</span><span class="sxs-lookup"><span data-stu-id="8c867-118">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8c867-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c867-119">See also</span></span>

- [<span data-ttu-id="8c867-120">查詢概念</span><span class="sxs-lookup"><span data-stu-id="8c867-120">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="8c867-121">物件識別</span><span class="sxs-lookup"><span data-stu-id="8c867-121">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [<span data-ttu-id="8c867-122">背景資訊</span><span class="sxs-lookup"><span data-stu-id="8c867-122">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="8c867-123">物件識別</span><span class="sxs-lookup"><span data-stu-id="8c867-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
