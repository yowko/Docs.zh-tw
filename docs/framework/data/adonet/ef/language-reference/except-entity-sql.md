---
title: EXCEPT (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de4455e997e0fc644fdc5bbef8ff52f84735d133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="except-entity-sql"></a><span data-ttu-id="a32d2-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a32d2-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="a32d2-103">從 EXCEPT 運算元左側的查詢運算式傳回任何相異值集合，這些相異值是 EXCEPT 運算元右側的查詢運算式沒有傳回的。</span><span class="sxs-lookup"><span data-stu-id="a32d2-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="a32d2-104">所有運算式都必須具有與 `expression`相同的型別或是共同基底型別或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="a32d2-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a32d2-105">語法</span><span class="sxs-lookup"><span data-stu-id="a32d2-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a32d2-106">引數</span><span class="sxs-lookup"><span data-stu-id="a32d2-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a32d2-107">任何有效的查詢運算式，該運算式會傳回要與另一個查詢運算式傳回之集合相比較的集合。</span><span class="sxs-lookup"><span data-stu-id="a32d2-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a32d2-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a32d2-108">Return Value</span></span>  
 <span data-ttu-id="a32d2-109">具有與 `expression`相同的型別或是共同基底類型或衍生型別的集合。</span><span class="sxs-lookup"><span data-stu-id="a32d2-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a32d2-110">備註</span><span class="sxs-lookup"><span data-stu-id="a32d2-110">Remarks</span></span>  
 <span data-ttu-id="a32d2-111">EXCEPT 是其中一個 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子。</span><span class="sxs-lookup"><span data-stu-id="a32d2-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="a32d2-112">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子都會從左到右評估。</span><span class="sxs-lookup"><span data-stu-id="a32d2-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="a32d2-113">下表顯示 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 設定運算子的優先順序。</span><span class="sxs-lookup"><span data-stu-id="a32d2-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="a32d2-114">優先順序</span><span class="sxs-lookup"><span data-stu-id="a32d2-114">Precedence</span></span>|<span data-ttu-id="a32d2-115">運算子</span><span class="sxs-lookup"><span data-stu-id="a32d2-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="a32d2-116">最高</span><span class="sxs-lookup"><span data-stu-id="a32d2-116">Highest</span></span>|<span data-ttu-id="a32d2-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="a32d2-117">INTERSECT</span></span>|  
||<span data-ttu-id="a32d2-118">UNION</span><span class="sxs-lookup"><span data-stu-id="a32d2-118">UNION</span></span><br /><br /> <span data-ttu-id="a32d2-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="a32d2-119">UNION ALL</span></span>|  
||<span data-ttu-id="a32d2-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="a32d2-120">EXCEPT</span></span>|  
|<span data-ttu-id="a32d2-121">最低</span><span class="sxs-lookup"><span data-stu-id="a32d2-121">Lowest</span></span>|<span data-ttu-id="a32d2-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="a32d2-122">EXISTS</span></span><br /><br /> <span data-ttu-id="a32d2-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="a32d2-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="a32d2-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="a32d2-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="a32d2-125">SET</span><span class="sxs-lookup"><span data-stu-id="a32d2-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a32d2-126">範例</span><span class="sxs-lookup"><span data-stu-id="a32d2-126">Example</span></span>  
 <span data-ttu-id="a32d2-127">下列 Entity SQL 查詢會使用 EXCEPT 運算子，從兩個查詢運算式傳回任何相異值的集合。</span><span class="sxs-lookup"><span data-stu-id="a32d2-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="a32d2-128">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="a32d2-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a32d2-129">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="a32d2-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a32d2-130">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="a32d2-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a32d2-131">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="a32d2-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="a32d2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a32d2-132">See Also</span></span>  
 [<span data-ttu-id="a32d2-133">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="a32d2-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
