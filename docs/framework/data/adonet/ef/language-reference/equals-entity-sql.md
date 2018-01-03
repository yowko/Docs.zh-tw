---
title: "= (等號) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c6b258bd06fd3e7e348e190b0897d66036006873
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="11713-102">= (等號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="11713-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="11713-103">比較兩個運算式是否相等。</span><span class="sxs-lookup"><span data-stu-id="11713-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11713-104">語法</span><span class="sxs-lookup"><span data-stu-id="11713-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="11713-105">引數</span><span class="sxs-lookup"><span data-stu-id="11713-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="11713-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="11713-106">Any valid expression.</span></span> <span data-ttu-id="11713-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="11713-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="11713-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="11713-108">Result Types</span></span>  
 <span data-ttu-id="11713-109">如果左運算式等於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="11713-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11713-110">備註</span><span class="sxs-lookup"><span data-stu-id="11713-110">Remarks</span></span>  
 <span data-ttu-id="11713-111">== 運算子就相當於 =。</span><span class="sxs-lookup"><span data-stu-id="11713-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11713-112">範例</span><span class="sxs-lookup"><span data-stu-id="11713-112">Example</span></span>  
 <span data-ttu-id="11713-113">以下 Entity SQL 查詢使用 = 比較運算子來比較兩個運算式是否相等。</span><span class="sxs-lookup"><span data-stu-id="11713-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="11713-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="11713-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="11713-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="11713-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="11713-116">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="11713-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="11713-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="11713-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="11713-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="11713-118">See Also</span></span>  
 [<span data-ttu-id="11713-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="11713-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
