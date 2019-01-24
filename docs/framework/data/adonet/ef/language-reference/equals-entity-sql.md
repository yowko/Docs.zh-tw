---
title: = (等號) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 2791bc0940bad92208c5bdce3659534f237bd6e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551874"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="ab2be-102">= (等號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ab2be-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="ab2be-103">比較兩個運算式是否相等。</span><span class="sxs-lookup"><span data-stu-id="ab2be-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab2be-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab2be-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ab2be-105">引數</span><span class="sxs-lookup"><span data-stu-id="ab2be-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ab2be-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="ab2be-106">Any valid expression.</span></span> <span data-ttu-id="ab2be-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="ab2be-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ab2be-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="ab2be-108">Result Types</span></span>  
 <span data-ttu-id="ab2be-109">如果左運算式等於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ab2be-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab2be-110">備註</span><span class="sxs-lookup"><span data-stu-id="ab2be-110">Remarks</span></span>  
 <span data-ttu-id="ab2be-111">== 運算子就相當於 =。</span><span class="sxs-lookup"><span data-stu-id="ab2be-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab2be-112">範例</span><span class="sxs-lookup"><span data-stu-id="ab2be-112">Example</span></span>  
 <span data-ttu-id="ab2be-113">以下 Entity SQL 查詢使用 = 比較運算子來比較兩個運算式是否相等。</span><span class="sxs-lookup"><span data-stu-id="ab2be-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="ab2be-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="ab2be-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ab2be-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="ab2be-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ab2be-116">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="ab2be-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ab2be-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="ab2be-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="ab2be-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab2be-118">See also</span></span>
- [<span data-ttu-id="ab2be-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="ab2be-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
