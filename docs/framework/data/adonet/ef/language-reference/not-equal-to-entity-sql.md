---
title: '!= (不等於) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 4ed09b0c5f10ef1ac77c4b374619508d714f1dc3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763692"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="c4aac-102">!= (不等於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c4aac-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="c4aac-103">比較兩個運算式來判斷左運算式是否不等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="c4aac-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="c4aac-104">!= (不等於) 運算子的功能相當於 <> 運算子。</span><span class="sxs-lookup"><span data-stu-id="c4aac-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4aac-105">語法</span><span class="sxs-lookup"><span data-stu-id="c4aac-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4aac-106">引數</span><span class="sxs-lookup"><span data-stu-id="c4aac-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c4aac-107">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4aac-107">Any valid expression.</span></span> <span data-ttu-id="c4aac-108">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="c4aac-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="c4aac-109">結果型別</span><span class="sxs-lookup"><span data-stu-id="c4aac-109">Result Types</span></span>  
 <span data-ttu-id="c4aac-110">如果左運算式不等於右運算式，則為`true` ，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c4aac-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4aac-111">範例</span><span class="sxs-lookup"><span data-stu-id="c4aac-111">Example</span></span>  
 <span data-ttu-id="c4aac-112">下列 Entity SQL 查詢使用 != 運算子來比較兩個運算式，以判斷左運算式是否不等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="c4aac-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="c4aac-113">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="c4aac-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c4aac-114">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="c4aac-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c4aac-115">遵循 [如何：執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="c4aac-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="c4aac-116">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="c4aac-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="c4aac-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4aac-117">See Also</span></span>  
 [<span data-ttu-id="c4aac-118">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="c4aac-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
