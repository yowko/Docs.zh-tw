---
title: '> （大於）（Entity SQL）'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: f2d3a0ed81cf75b7e567dbd07e119629ea47ac69
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833764"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="60fe4-102">> （大於）（Entity SQL）</span><span class="sxs-lookup"><span data-stu-id="60fe4-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="60fe4-103">比較兩個運算式來判斷左運算式的值是否大於右運算式。</span><span class="sxs-lookup"><span data-stu-id="60fe4-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60fe4-104">語法</span><span class="sxs-lookup"><span data-stu-id="60fe4-104">Syntax</span></span>  
  
```sql  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="60fe4-105">引數</span><span class="sxs-lookup"><span data-stu-id="60fe4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="60fe4-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="60fe4-106">Any valid expression.</span></span> <span data-ttu-id="60fe4-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="60fe4-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="60fe4-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="60fe4-108">Result Types</span></span>  
 <span data-ttu-id="60fe4-109">如果左運算式的值大於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="60fe4-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60fe4-110">範例</span><span class="sxs-lookup"><span data-stu-id="60fe4-110">Example</span></span>  
 <span data-ttu-id="60fe4-111">下列 Entity SQL 查詢使用 > 比較運算子來比較兩個運算式，以判斷左運算式的值是否大於右運算式。</span><span class="sxs-lookup"><span data-stu-id="60fe4-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="60fe4-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="60fe4-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="60fe4-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="60fe4-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="60fe4-114">依照 [How 中的程式進行：執行可傳回 StructuralType 結果 @ no__t-0 的查詢。</span><span class="sxs-lookup"><span data-stu-id="60fe4-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="60fe4-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="60fe4-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#GREATER](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="60fe4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60fe4-116">See also</span></span>

- [<span data-ttu-id="60fe4-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="60fe4-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
