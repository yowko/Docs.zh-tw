---
title: < = （小於或等於）（Entity SQL）
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: b3c8fef47b06b9fdd0a1619a9e56d3d916d9dd2d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319640"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="3cd21-102">\<= (小於或等於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3cd21-102">\<= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="3cd21-103">比較兩個運算式來判斷左運算式的值是否小於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="3cd21-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cd21-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cd21-104">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="3cd21-105">引數</span><span class="sxs-lookup"><span data-stu-id="3cd21-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3cd21-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="3cd21-106">Any valid expression.</span></span> <span data-ttu-id="3cd21-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="3cd21-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="3cd21-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="3cd21-108">Result Types</span></span>  
 <span data-ttu-id="3cd21-109">如果左運算式的值小於或等於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="3cd21-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cd21-110">範例</span><span class="sxs-lookup"><span data-stu-id="3cd21-110">Example</span></span>  
 <span data-ttu-id="3cd21-111">下列 Entity SQL 查詢使用 <= 比較運算子來比較兩個運算式，以判斷左運算式的值是否小於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="3cd21-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="3cd21-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="3cd21-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3cd21-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="3cd21-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3cd21-114">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="3cd21-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3cd21-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="3cd21-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="3cd21-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="3cd21-116">See also</span></span>

- [<span data-ttu-id="3cd21-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="3cd21-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
