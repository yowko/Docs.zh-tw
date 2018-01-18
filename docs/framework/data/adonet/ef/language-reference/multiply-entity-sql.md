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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c7e2bcf15ab8d0cf24fdc6cb7e9db025784bd435
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="fe736-102">\* (乘號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fe736-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="fe736-103">將兩個運算式相乘。</span><span class="sxs-lookup"><span data-stu-id="fe736-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe736-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe736-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fe736-105">引數</span><span class="sxs-lookup"><span data-stu-id="fe736-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fe736-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="fe736-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fe736-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="fe736-107">Result Types</span></span>  
 <span data-ttu-id="fe736-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="fe736-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="fe736-109">如需隱含類型提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="fe736-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe736-110">範例</span><span class="sxs-lookup"><span data-stu-id="fe736-110">Example</span></span>  
 <span data-ttu-id="fe736-111">下列 Entity SQL 查詢會使用 \* 算術運算子讓兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="fe736-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="fe736-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="fe736-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fe736-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="fe736-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fe736-114">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="fe736-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="fe736-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="fe736-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="fe736-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe736-116">See Also</span></span>  
 [<span data-ttu-id="fe736-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="fe736-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
