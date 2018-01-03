---
title: "- （負）(Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 78d5ccbcfe23acd1a8b9b285d865452e7ccad00f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="fbb24-102">- (負號) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fbb24-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="fbb24-103">傳回數值運算式的負值。</span><span class="sxs-lookup"><span data-stu-id="fbb24-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb24-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbb24-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fbb24-105">引數</span><span class="sxs-lookup"><span data-stu-id="fbb24-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fbb24-106">任何一個數值資料型別的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="fbb24-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fbb24-107">結果型別</span><span class="sxs-lookup"><span data-stu-id="fbb24-107">Result Types</span></span>  
 <span data-ttu-id="fbb24-108">`expression`的資料型別。</span><span class="sxs-lookup"><span data-stu-id="fbb24-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbb24-109">備註</span><span class="sxs-lookup"><span data-stu-id="fbb24-109">Remarks</span></span>  
 <span data-ttu-id="fbb24-110">如果 `expression` 是不帶正負號型別，結果型別就是與 `expression`型別最密切相關的帶正負號型別。</span><span class="sxs-lookup"><span data-stu-id="fbb24-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="fbb24-111">例如，如果 `expression` 的型別為 Byte，就會傳回 Int16 型別的值。</span><span class="sxs-lookup"><span data-stu-id="fbb24-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbb24-112">範例</span><span class="sxs-lookup"><span data-stu-id="fbb24-112">Example</span></span>  
 <span data-ttu-id="fbb24-113">下列 Entity SQL 查詢會使用 - 算術運算子來傳回數值運算式的負值。</span><span class="sxs-lookup"><span data-stu-id="fbb24-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="fbb24-114">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="fbb24-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fbb24-115">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="fbb24-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fbb24-116">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="fbb24-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="fbb24-117">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="fbb24-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="fbb24-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbb24-118">See Also</span></span>  
 [<span data-ttu-id="fbb24-119">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="fbb24-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
