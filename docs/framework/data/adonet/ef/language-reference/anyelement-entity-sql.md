---
title: ANYELEMENT (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e74fbac9c2c57c653f55f76bf165d7eaebd9cee
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="anyelement-entity-sql"></a><span data-ttu-id="88a51-102">ANYELEMENT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="88a51-102">ANYELEMENT (Entity SQL)</span></span>
<span data-ttu-id="88a51-103">從多重值集合中擷取元素。</span><span class="sxs-lookup"><span data-stu-id="88a51-103">Extracts an element from a multivalued collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a51-104">語法</span><span class="sxs-lookup"><span data-stu-id="88a51-104">Syntax</span></span>  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="88a51-105">引數</span><span class="sxs-lookup"><span data-stu-id="88a51-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="88a51-106">傳回可從中擷取元素之集合的任何有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="88a51-106">Any valid query expression that returns a collection to extract an element from.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88a51-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="88a51-107">Return Value</span></span>  
 <span data-ttu-id="88a51-108">如果集合具有多個元素，就是集合中的單一元素或任意元素。如果集合是空的，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="88a51-108">A single element in the collection or an arbitrary element if the collection has more than one; if the collection is empty, returns `null`.</span></span> <span data-ttu-id="88a51-109">如果`collection`是集合型別的`Collection<T>`，然後`ANYELEMENT(collection)`是有效的運算式可產生執行個體的型別`T`。</span><span class="sxs-lookup"><span data-stu-id="88a51-109">If `collection` is a collection of type `Collection<T>`, then `ANYELEMENT(collection)` is a valid expression that yields an instance of type `T`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88a51-110">備註</span><span class="sxs-lookup"><span data-stu-id="88a51-110">Remarks</span></span>  
 <span data-ttu-id="88a51-111">ANYELEMENT 會從多重值集合中擷取任意元素。</span><span class="sxs-lookup"><span data-stu-id="88a51-111">ANYELEMENT extracts an arbitrary element from a multivalued collection.</span></span> <span data-ttu-id="88a51-112">例如，下列範例會嘗試從 `Customers`集合中擷取單一元素。</span><span class="sxs-lookup"><span data-stu-id="88a51-112">For example, the following example attempts to extract a singleton element from the set `Customers`.</span></span>  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a><span data-ttu-id="88a51-113">範例</span><span class="sxs-lookup"><span data-stu-id="88a51-113">Example</span></span>  
 <span data-ttu-id="88a51-114">下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢會使用 ANYELEMENT 運算子，從多重值集合中擷取元素。</span><span class="sxs-lookup"><span data-stu-id="88a51-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ANYELEMENT operator to extract an element from a multivalued collection.</span></span> <span data-ttu-id="88a51-115">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="88a51-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="88a51-116">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="88a51-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="88a51-117">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="88a51-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="88a51-118">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="88a51-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a><span data-ttu-id="88a51-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="88a51-119">See Also</span></span>  
 [<span data-ttu-id="88a51-120">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="88a51-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="88a51-121">可為 Null 的結構類型</span><span class="sxs-lookup"><span data-stu-id="88a51-121">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
