---
title: + （新增）
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: f095703646d5280947e67a6640d49234a4da3622
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826742"
---
# <a name="-add"></a><span data-ttu-id="4eb77-102">+ (加號)</span><span class="sxs-lookup"><span data-stu-id="4eb77-102">+ (Add)</span></span>
<span data-ttu-id="4eb77-103">將兩個數字相加。</span><span class="sxs-lookup"><span data-stu-id="4eb77-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eb77-104">語法</span><span class="sxs-lookup"><span data-stu-id="4eb77-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4eb77-105">引數</span><span class="sxs-lookup"><span data-stu-id="4eb77-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4eb77-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="4eb77-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4eb77-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="4eb77-107">Result Types</span></span>  
 <span data-ttu-id="4eb77-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="4eb77-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="4eb77-109">如需有關隱含型別提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="4eb77-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4eb77-110">備註</span><span class="sxs-lookup"><span data-stu-id="4eb77-110">Remarks</span></span>  
 <span data-ttu-id="4eb77-111">若為 EDM.String 型別，加法就會串連。</span><span class="sxs-lookup"><span data-stu-id="4eb77-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4eb77-112">範例</span><span class="sxs-lookup"><span data-stu-id="4eb77-112">Example</span></span>  
 <span data-ttu-id="4eb77-113">下列 Entity SQL 查詢會使用 + 算術運算子讓兩個數字相加。</span><span class="sxs-lookup"><span data-stu-id="4eb77-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="4eb77-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="4eb77-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4eb77-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="4eb77-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4eb77-116">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="4eb77-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4eb77-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="4eb77-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="4eb77-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4eb77-118">See also</span></span>
- [<span data-ttu-id="4eb77-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="4eb77-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="4eb77-120">概念模型類型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="4eb77-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
