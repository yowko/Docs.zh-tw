---
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: e46db63600b6baa03697615a2f5eb9240f55d15e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833686"
---
# <a name="in-entity-sql"></a><span data-ttu-id="0439a-102">IN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0439a-102">IN (Entity SQL)</span></span>
<span data-ttu-id="0439a-103">判斷某個值是否與集合中的任何值相符。</span><span class="sxs-lookup"><span data-stu-id="0439a-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0439a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0439a-104">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0439a-105">引數</span><span class="sxs-lookup"><span data-stu-id="0439a-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="0439a-106">傳回要比對之值的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="0439a-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="0439a-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="0439a-107">[ NOT ]</span></span>  
 <span data-ttu-id="0439a-108">指定 IN 的 `Boolean` 結果是負值。</span><span class="sxs-lookup"><span data-stu-id="0439a-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="0439a-109">傳回要測試是否有相符項目之集合的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="0439a-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="0439a-110">所有運算式都必須具有與 `value`相同的型別或是共同基底型別或衍生型別。</span><span class="sxs-lookup"><span data-stu-id="0439a-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0439a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="0439a-111">Return Value</span></span>  
 <span data-ttu-id="0439a-112">如果在集合中找到值，就是 `true`。如果此值為 null 或集合為 null，就是 null，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="0439a-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="0439a-113">使用 NOT IN 會執行 IN 結果的否定運算。</span><span class="sxs-lookup"><span data-stu-id="0439a-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0439a-114">範例</span><span class="sxs-lookup"><span data-stu-id="0439a-114">Example</span></span>  
 <span data-ttu-id="0439a-115">下列 Entity SQL 查詢會使用 IN 運算子來判斷某個值是否與集合中的任何值相符。</span><span class="sxs-lookup"><span data-stu-id="0439a-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="0439a-116">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="0439a-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0439a-117">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="0439a-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="0439a-118">依照 [How 中的程式進行：執行可傳回 StructuralType 結果 @ no__t-0 的查詢。</span><span class="sxs-lookup"><span data-stu-id="0439a-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="0439a-119">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="0439a-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="0439a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0439a-120">See also</span></span>

- [<span data-ttu-id="0439a-121">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="0439a-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
