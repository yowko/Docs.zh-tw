---
title: + （字串串連）(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 8a1785d590c5f7fcc443856180d516bb40cfc28e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408470"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="9d5e4-102">+ (字串串連) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9d5e4-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="9d5e4-103">串連兩個字串。</span><span class="sxs-lookup"><span data-stu-id="9d5e4-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d5e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d5e4-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9d5e4-105">引數</span><span class="sxs-lookup"><span data-stu-id="9d5e4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9d5e4-106">EDM.String 資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="9d5e4-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="9d5e4-107">兩個運算式的資料型別必須相同，或者其中一個運算式必須可以用隱含方式轉換為另一個運算式的資料型別。</span><span class="sxs-lookup"><span data-stu-id="9d5e4-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9d5e4-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="9d5e4-108">Result Types</span></span>  
 <span data-ttu-id="9d5e4-109">從兩個引數的隱含型別提升產生的資料型別。</span><span class="sxs-lookup"><span data-stu-id="9d5e4-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="9d5e4-110">如需有關隱含型別提升的詳細資訊，請參閱[型別系統](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="9d5e4-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d5e4-111">範例</span><span class="sxs-lookup"><span data-stu-id="9d5e4-111">Example</span></span>  
 <span data-ttu-id="9d5e4-112">下列 Entity SQL 查詢會使用 + 運算子來串連兩個字串。</span><span class="sxs-lookup"><span data-stu-id="9d5e4-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="9d5e4-113">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="9d5e4-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9d5e4-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="9d5e4-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="9d5e4-115">請依照下列中的程序[如何： 執行查詢，傳回 PrimitiveType 結果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="9d5e4-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="9d5e4-116">將下列查詢當成引數，傳遞至 `ExecutePrimitiveTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="9d5e4-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="9d5e4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d5e4-117">See Also</span></span>  
 [<span data-ttu-id="9d5e4-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="9d5e4-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="9d5e4-119">概念模型型別 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="9d5e4-119">Conceptual Model Types (CSDL)</span></span>](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
