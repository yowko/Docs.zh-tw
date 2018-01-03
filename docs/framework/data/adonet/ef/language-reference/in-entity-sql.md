---
title: IN (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 00d5a309a68ad7c1c5f363d6df3cca7a0e90ce81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="in-entity-sql"></a><span data-ttu-id="c0d5d-102">IN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c0d5d-102">IN (Entity SQL)</span></span>
<span data-ttu-id="c0d5d-103">判斷某個值是否與集合中的任何值相符。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0d5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0d5d-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c0d5d-105">引數</span><span class="sxs-lookup"><span data-stu-id="c0d5d-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="c0d5d-106">傳回要比對之值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="c0d5d-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="c0d5d-107">[ NOT ]</span></span>  
 <span data-ttu-id="c0d5d-108">指定 IN 的 `Boolean` 結果是負值。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="c0d5d-109">傳回要測試是否有相符項目之集合的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="c0d5d-110">所有運算式都必須具有與 `value` 相同的型別或是共同基底型別或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0d5d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c0d5d-111">Return Value</span></span>  
 <span data-ttu-id="c0d5d-112">如果在集合中找到值，就是 `true`。如果此值為 null 或集合為 null，就是 null，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="c0d5d-113">使用 NOT IN 會執行 IN 結果的否定運算。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0d5d-114">範例</span><span class="sxs-lookup"><span data-stu-id="c0d5d-114">Example</span></span>  
 <span data-ttu-id="c0d5d-115">下列 Entity SQL 查詢會使用 IN 運算子來判斷某個值是否與集合中的任何值相符。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="c0d5d-116">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c0d5d-117">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="c0d5d-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c0d5d-118">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="c0d5d-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="c0d5d-119">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="c0d5d-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="c0d5d-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0d5d-120">See Also</span></span>  
 [<span data-ttu-id="c0d5d-121">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="c0d5d-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
