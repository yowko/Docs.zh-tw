---
title: + (加)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b86d273658362c3bb204d5220ff5e9db1f8de9fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198050"
---
# <a name="-add"></a><span data-ttu-id="911ce-102">+ (加號)</span><span class="sxs-lookup"><span data-stu-id="911ce-102">+ (Add)</span></span>

<span data-ttu-id="911ce-103">兩個數字相加。</span><span class="sxs-lookup"><span data-stu-id="911ce-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="911ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="911ce-104">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="911ce-105">引數</span><span class="sxs-lookup"><span data-stu-id="911ce-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="911ce-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="911ce-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="911ce-107">結果類型</span><span class="sxs-lookup"><span data-stu-id="911ce-107">Result Types</span></span>  

 <span data-ttu-id="911ce-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="911ce-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="911ce-109">如需隱含類型升級的詳細資訊，請參閱 [類型系統](type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="911ce-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="911ce-110">備註</span><span class="sxs-lookup"><span data-stu-id="911ce-110">Remarks</span></span>  

 <span data-ttu-id="911ce-111">若為 EDM.String 型別，加法就會串連。</span><span class="sxs-lookup"><span data-stu-id="911ce-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="911ce-112">範例</span><span class="sxs-lookup"><span data-stu-id="911ce-112">Example</span></span>  

 <span data-ttu-id="911ce-113">下列 Entity SQL 查詢會使用 + 算術運算子讓兩個數字相加。</span><span class="sxs-lookup"><span data-stu-id="911ce-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="911ce-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="911ce-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="911ce-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="911ce-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="911ce-116">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="911ce-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="911ce-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="911ce-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="911ce-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="911ce-118">See also</span></span>

- [<span data-ttu-id="911ce-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="911ce-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="911ce-120">概念模型類型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="911ce-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
