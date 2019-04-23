---
title: -- (註解) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: c10b17931c6024e2a9e947083747435d8aa54fa2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339511"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="6483c-102">-- (註解) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6483c-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="6483c-103">查詢可以包含註解。</span><span class="sxs-lookup"><span data-stu-id="6483c-103">queries can contain comments.</span></span> <span data-ttu-id="6483c-104">兩個破折號 (`--`) 就代表註解行的開始。</span><span class="sxs-lookup"><span data-stu-id="6483c-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6483c-105">語法</span><span class="sxs-lookup"><span data-stu-id="6483c-105">Syntax</span></span>  
  
```  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="6483c-106">引數</span><span class="sxs-lookup"><span data-stu-id="6483c-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="6483c-107">這是包含註解文字的字元字串。</span><span class="sxs-lookup"><span data-stu-id="6483c-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6483c-108">範例</span><span class="sxs-lookup"><span data-stu-id="6483c-108">Example</span></span>  
 <span data-ttu-id="6483c-109">以下 Entity SQL 查詢示範如何使用註解。</span><span class="sxs-lookup"><span data-stu-id="6483c-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="6483c-110">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="6483c-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6483c-111">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="6483c-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6483c-112">請依照下列中的程序[How to:執行可傳回 StructuralType 結果的查詢](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="6483c-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6483c-113">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="6483c-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="6483c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6483c-114">See also</span></span>

- [<span data-ttu-id="6483c-115">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="6483c-115">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="6483c-116">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="6483c-116">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
