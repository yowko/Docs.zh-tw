---
title: + （字串串連）(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: b1416649681aed7ef730e9d17c3863a6616ab37f
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903638"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="9df98-102">+ (字串串連) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9df98-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="9df98-103">串連兩個字串。</span><span class="sxs-lookup"><span data-stu-id="9df98-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df98-104">語法</span><span class="sxs-lookup"><span data-stu-id="9df98-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9df98-105">引數</span><span class="sxs-lookup"><span data-stu-id="9df98-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9df98-106">EDM.String 資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="9df98-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="9df98-107">兩個運算式的資料型別必須相同，或者其中一個運算式必須可以用隱含方式轉換為另一個運算式的資料型別。</span><span class="sxs-lookup"><span data-stu-id="9df98-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9df98-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="9df98-108">Result Types</span></span>  
 <span data-ttu-id="9df98-109">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="9df98-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="9df98-110">如需有關隱含型別提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="9df98-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9df98-111">範例</span><span class="sxs-lookup"><span data-stu-id="9df98-111">Example</span></span>  
 <span data-ttu-id="9df98-112">下列 Entity SQL 查詢會使用 + 運算子來串連兩個字串。</span><span class="sxs-lookup"><span data-stu-id="9df98-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="9df98-113">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="9df98-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9df98-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="9df98-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9df98-115">請依照下列中的程序[How to:執行可傳回 PrimitiveType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="9df98-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="9df98-116">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="9df98-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="9df98-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9df98-117">See also</span></span>
- [<span data-ttu-id="9df98-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9df98-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="9df98-119">概念模型類型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="9df98-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
