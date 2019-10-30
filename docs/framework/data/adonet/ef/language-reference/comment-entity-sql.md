---
title: -- (註解) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5d9de735-2099-47f1-b7e7-60856f494924
ms.openlocfilehash: 43b8cdbf5dbca8822645c27711f6984b8d741ea7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040279"
---
# <a name="---comment-entity-sql"></a><span data-ttu-id="6a2f8-102">-- (註解) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6a2f8-102">-- (Comment) (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="6a2f8-103">查詢可以包含註解。</span><span class="sxs-lookup"><span data-stu-id="6a2f8-103">queries can contain comments.</span></span> <span data-ttu-id="6a2f8-104">兩個破折號 (`--`) 就代表註解行的開始。</span><span class="sxs-lookup"><span data-stu-id="6a2f8-104">Two dashes (`--`) start a comment line.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a2f8-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a2f8-105">Syntax</span></span>  
  
```csharp  
-- text_of_comment  
```  
  
## <a name="arguments"></a><span data-ttu-id="6a2f8-106">引數</span><span class="sxs-lookup"><span data-stu-id="6a2f8-106">Arguments</span></span>  
 `text_of_comment`  
 <span data-ttu-id="6a2f8-107">這是包含註解文字的字元字串。</span><span class="sxs-lookup"><span data-stu-id="6a2f8-107">Is the character string that contains the text of the comment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a2f8-108">範例</span><span class="sxs-lookup"><span data-stu-id="6a2f8-108">Example</span></span>  
 <span data-ttu-id="6a2f8-109">以下 Entity SQL 查詢示範如何使用註解。</span><span class="sxs-lookup"><span data-stu-id="6a2f8-109">The following Entity SQL query demonstrates how to use comments.</span></span> <span data-ttu-id="6a2f8-110">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="6a2f8-110">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6a2f8-111">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="6a2f8-111">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6a2f8-112">遵循 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的程序進行。</span><span class="sxs-lookup"><span data-stu-id="6a2f8-112">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6a2f8-113">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="6a2f8-113">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#COMMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#comment)]  
  
## <a name="see-also"></a><span data-ttu-id="6a2f8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6a2f8-114">See also</span></span>

- [<span data-ttu-id="6a2f8-115">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="6a2f8-115">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="6a2f8-116">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="6a2f8-116">Entity SQL Reference</span></span>](entity-sql-reference.md)
