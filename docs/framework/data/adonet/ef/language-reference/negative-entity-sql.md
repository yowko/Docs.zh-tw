---
title: '- 負極（Entity SQL）'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 7716b9115587a873531be9c14b7da93c7a148ed8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319530"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="f513a-102">- (負號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f513a-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="f513a-103">傳回數值運算式的負值。</span><span class="sxs-lookup"><span data-stu-id="f513a-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f513a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f513a-104">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f513a-105">引數</span><span class="sxs-lookup"><span data-stu-id="f513a-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f513a-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="f513a-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f513a-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="f513a-107">Result Types</span></span>  
 <span data-ttu-id="f513a-108">`expression`的資料型別。</span><span class="sxs-lookup"><span data-stu-id="f513a-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f513a-109">備註</span><span class="sxs-lookup"><span data-stu-id="f513a-109">Remarks</span></span>  
 <span data-ttu-id="f513a-110">如果 `expression` 是不帶正負號型別，結果型別就是與 `expression`型別最密切相關的帶正負號型別。</span><span class="sxs-lookup"><span data-stu-id="f513a-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="f513a-111">例如，如果 `expression` 的型別為 Byte，就會傳回 Int16 型別的值。</span><span class="sxs-lookup"><span data-stu-id="f513a-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f513a-112">範例</span><span class="sxs-lookup"><span data-stu-id="f513a-112">Example</span></span>  
 <span data-ttu-id="f513a-113">下列 Entity SQL 查詢會使用 - 算術運算子來傳回數值運算式的負值。</span><span class="sxs-lookup"><span data-stu-id="f513a-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="f513a-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="f513a-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f513a-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="f513a-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f513a-116">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="f513a-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f513a-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="f513a-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="f513a-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="f513a-118">See also</span></span>

- [<span data-ttu-id="f513a-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="f513a-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
