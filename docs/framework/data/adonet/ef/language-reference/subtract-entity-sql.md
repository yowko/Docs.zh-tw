---
title: "- （減）(Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 20b9fd7dda34d3f6f19551d8f7e313196e0acc12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="82c5b-102">- (減號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="82c5b-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="82c5b-103">兩個數字相減。</span><span class="sxs-lookup"><span data-stu-id="82c5b-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="82c5b-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="82c5b-105">引數</span><span class="sxs-lookup"><span data-stu-id="82c5b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="82c5b-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="82c5b-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="82c5b-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="82c5b-107">Result Types</span></span>  
 <span data-ttu-id="82c5b-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="82c5b-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="82c5b-109">如需隱含類型提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="82c5b-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82c5b-110">範例</span><span class="sxs-lookup"><span data-stu-id="82c5b-110">Example</span></span>  
 <span data-ttu-id="82c5b-111">下列 Entity SQL 查詢會使用 - 算術運算子讓兩個數字相減。</span><span class="sxs-lookup"><span data-stu-id="82c5b-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="82c5b-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="82c5b-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="82c5b-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="82c5b-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="82c5b-114">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="82c5b-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="82c5b-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="82c5b-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="82c5b-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="82c5b-116">See Also</span></span>  
 [<span data-ttu-id="82c5b-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="82c5b-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
