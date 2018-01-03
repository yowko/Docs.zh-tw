---
title: "&gt;= (大於或等於) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 89e24b3e1a4b707ca60d798889538eb1bcd6a3bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="gt-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="83413-102">&gt;= (大於或等於) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="83413-102">&gt;= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="83413-103">比較兩個運算式來判斷左運算式的值是否大於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="83413-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83413-104">語法</span><span class="sxs-lookup"><span data-stu-id="83413-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="83413-105">引數</span><span class="sxs-lookup"><span data-stu-id="83413-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="83413-106">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="83413-106">Any valid expression.</span></span> <span data-ttu-id="83413-107">兩個運算式都必須有可隱含轉換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="83413-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="83413-108">結果型別</span><span class="sxs-lookup"><span data-stu-id="83413-108">Result Types</span></span>  
 <span data-ttu-id="83413-109">如果左運算式的值大於或等於右運算式則為`true` ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="83413-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83413-110">範例</span><span class="sxs-lookup"><span data-stu-id="83413-110">Example</span></span>  
 <span data-ttu-id="83413-111">下列 Entity SQL 查詢使用 >= 比較運算子來比較兩個運算式，以判斷左運算式的值是否大於或等於右運算式。</span><span class="sxs-lookup"><span data-stu-id="83413-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="83413-112">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="83413-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="83413-113">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="83413-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="83413-114">遵循 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="83413-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="83413-115">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="83413-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="83413-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="83413-116">See Also</span></span>  
 [<span data-ttu-id="83413-117">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="83413-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
