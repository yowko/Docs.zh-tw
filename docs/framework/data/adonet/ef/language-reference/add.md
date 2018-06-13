---
title: + （新增）
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: fcdee9388963553fef377a887d2e07161353f6c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761723"
---
# <a name="-add"></a><span data-ttu-id="1cea5-102">+ (加號)</span><span class="sxs-lookup"><span data-stu-id="1cea5-102">+ (Add)</span></span>
<span data-ttu-id="1cea5-103">將兩個數字相加。</span><span class="sxs-lookup"><span data-stu-id="1cea5-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cea5-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cea5-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1cea5-105">引數</span><span class="sxs-lookup"><span data-stu-id="1cea5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1cea5-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="1cea5-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1cea5-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="1cea5-107">Result Types</span></span>  
 <span data-ttu-id="1cea5-108">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="1cea5-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="1cea5-109">如需隱含類型提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="1cea5-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cea5-110">備註</span><span class="sxs-lookup"><span data-stu-id="1cea5-110">Remarks</span></span>  
 <span data-ttu-id="1cea5-111">若為 EDM.String 型別，加法就會串連。</span><span class="sxs-lookup"><span data-stu-id="1cea5-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cea5-112">範例</span><span class="sxs-lookup"><span data-stu-id="1cea5-112">Example</span></span>  
 <span data-ttu-id="1cea5-113">下列 Entity SQL 查詢會使用 + 算術運算子讓兩個數字相加。</span><span class="sxs-lookup"><span data-stu-id="1cea5-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="1cea5-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="1cea5-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1cea5-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="1cea5-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1cea5-116">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="1cea5-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="1cea5-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="1cea5-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="1cea5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cea5-118">See Also</span></span>  
 [<span data-ttu-id="1cea5-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="1cea5-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="1cea5-120">概念模型類型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="1cea5-120">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
