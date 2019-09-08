---
title: 從識別快取擷取物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: d14b15f72bd196d8b3a61f22c614516e17d2e95b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781236"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="ab6b8-102">從識別快取擷取物件</span><span class="sxs-lookup"><span data-stu-id="ab6b8-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="ab6b8-103">本主題描述 LINQ to SQL 查詢的類型，這些查詢可從 <xref:System.Data.Linq.DataContext> 所管理的識別快取傳回物件。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="ab6b8-104">在 LINQ to SQL 中，<xref:System.Data.Linq.DataContext> 用來管理物件的其中一種方式就是在執行查詢時，將物件識別記錄在識別快取中。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="ab6b8-105">在某些情況下，LINQ to SQL 會先嘗試從識別快取擷取物件，然後再執行資料庫的查詢。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="ab6b8-106">一般而言，為了讓 LINQ to SQL 查詢從識別快取傳回物件，此查詢必須以物件的主索引鍵為基礎，而且必須傳回單一物件。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="ab6b8-107">特別是，此查詢必須採用下列其中一種一般格式。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ab6b8-108">預先編譯的查詢不會從識別快取傳回物件。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="ab6b8-109">如需預先編譯查詢的詳細資訊，請<xref:System.Data.Linq.CompiledQuery>參閱[和如何：儲存和重複使用](how-to-store-and-reuse-queries.md)查詢。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="ab6b8-110">若要從識別快取擷取物件，查詢必須採用下列其中一種一般格式：</span><span class="sxs-lookup"><span data-stu-id="ab6b8-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="ab6b8-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="ab6b8-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="ab6b8-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="ab6b8-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="ab6b8-113">在這些一般格式中，`Function1`、`Function2` 和 `predicate` 的定義方式如下。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="ab6b8-114">`Function1` 可以是下列任何項目：</span><span class="sxs-lookup"><span data-stu-id="ab6b8-114">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="ab6b8-115">`Function2` 可以是下列任何項目：</span><span class="sxs-lookup"><span data-stu-id="ab6b8-115">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="ab6b8-116">`predicate` 必須是物件之主索引鍵屬性設定為常數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="ab6b8-117">如果物件具有多個屬性所定義的主索引鍵，每個主索引鍵屬性都必須設定為常數值。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="ab6b8-118">下面是 `predicate` 必須採用的格式範例：</span><span class="sxs-lookup"><span data-stu-id="ab6b8-118">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="ab6b8-119">範例</span><span class="sxs-lookup"><span data-stu-id="ab6b8-119">Example</span></span>  
 <span data-ttu-id="ab6b8-120">下列程式碼將提供 LINQ to SQL 查詢類型的範例，這些查詢可從識別快取擷取物件。</span><span class="sxs-lookup"><span data-stu-id="ab6b8-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ab6b8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab6b8-121">See also</span></span>

- [<span data-ttu-id="ab6b8-122">查詢概念</span><span class="sxs-lookup"><span data-stu-id="ab6b8-122">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="ab6b8-123">物件身分識別</span><span class="sxs-lookup"><span data-stu-id="ab6b8-123">Object Identity</span></span>](object-identity.md)
- [<span data-ttu-id="ab6b8-124">背景資訊</span><span class="sxs-lookup"><span data-stu-id="ab6b8-124">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="ab6b8-125">物件身分識別</span><span class="sxs-lookup"><span data-stu-id="ab6b8-125">Object Identity</span></span>](object-identity.md)
