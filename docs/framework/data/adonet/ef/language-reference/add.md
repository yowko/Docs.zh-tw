---
title: + (加號)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: 8c9a6b2c8168e4677c37cfdb0b401a93ee0040cf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251363"
---
# <a name="-add"></a><span data-ttu-id="bf0f3-102">+ (加號)</span><span class="sxs-lookup"><span data-stu-id="bf0f3-102">+ (Add)</span></span>
<span data-ttu-id="bf0f3-103">將兩個數字相加。</span><span class="sxs-lookup"><span data-stu-id="bf0f3-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf0f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="bf0f3-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="bf0f3-105">引數</span><span class="sxs-lookup"><span data-stu-id="bf0f3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bf0f3-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="bf0f3-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="bf0f3-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="bf0f3-107">Result Types</span></span>  
 <span data-ttu-id="bf0f3-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="bf0f3-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="bf0f3-109">如需隱含類型升級的詳細資訊, 請參閱[類型系統](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="bf0f3-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf0f3-110">備註</span><span class="sxs-lookup"><span data-stu-id="bf0f3-110">Remarks</span></span>  
 <span data-ttu-id="bf0f3-111">若為 EDM.String 型別，加法就會串連。</span><span class="sxs-lookup"><span data-stu-id="bf0f3-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf0f3-112">範例</span><span class="sxs-lookup"><span data-stu-id="bf0f3-112">Example</span></span>  
 <span data-ttu-id="bf0f3-113">下列 Entity SQL 查詢會使用 + 算術運算子讓兩個數字相加。</span><span class="sxs-lookup"><span data-stu-id="bf0f3-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="bf0f3-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="bf0f3-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bf0f3-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="bf0f3-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="bf0f3-116">[遵循 how to:執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="bf0f3-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="bf0f3-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="bf0f3-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="bf0f3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf0f3-118">See also</span></span>

- [<span data-ttu-id="bf0f3-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="bf0f3-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="bf0f3-120">概念模型類型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="bf0f3-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
