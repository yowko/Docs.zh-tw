---
title: "* （乘）(Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47ccf810dde528af757f9c5698950198224b3118
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="76ae8-102">* (乘號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="76ae8-102">* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="76ae8-103">將兩個運算式相乘。</span><span class="sxs-lookup"><span data-stu-id="76ae8-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ae8-104">語法</span><span class="sxs-lookup"><span data-stu-id="76ae8-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="76ae8-105">引數</span><span class="sxs-lookup"><span data-stu-id="76ae8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="76ae8-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="76ae8-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="76ae8-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="76ae8-107">Result Types</span></span>  
 <span data-ttu-id="76ae8-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="76ae8-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="76ae8-109">如需隱含類型提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="76ae8-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76ae8-110">範例</span><span class="sxs-lookup"><span data-stu-id="76ae8-110">Example</span></span>  
 <span data-ttu-id="76ae8-111">下列 Entity SQL 查詢會使用 * 算術運算子讓兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="76ae8-111">The following Entity SQL query uses the * arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="76ae8-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="76ae8-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="76ae8-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="76ae8-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="76ae8-114">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="76ae8-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="76ae8-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="76ae8-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="76ae8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76ae8-116">See Also</span></span>  
 [<span data-ttu-id="76ae8-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="76ae8-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
