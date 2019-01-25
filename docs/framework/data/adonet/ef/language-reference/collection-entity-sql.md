---
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: d4e52bb62412e61e1a71e0fe9a8555068ca18dbd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506455"
---
# <a name="collection-entity-sql"></a><span data-ttu-id="135a7-102">COLLECTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="135a7-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="135a7-103">COLLECTION 關鍵字只用於內嵌函式的定義。</span><span class="sxs-lookup"><span data-stu-id="135a7-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="135a7-104">集合函式是處理值的集合並產生純量輸出的函式。</span><span class="sxs-lookup"><span data-stu-id="135a7-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="135a7-105">語法</span><span class="sxs-lookup"><span data-stu-id="135a7-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="135a7-106">引數</span><span class="sxs-lookup"><span data-stu-id="135a7-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="135a7-107">傳回支援的型別、資料列或參考等集合的運算式。</span><span class="sxs-lookup"><span data-stu-id="135a7-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="135a7-108">備註</span><span class="sxs-lookup"><span data-stu-id="135a7-108">Remarks</span></span>  
 <span data-ttu-id="135a7-109">如需 COLLECTION 關鍵字的詳細資訊，請參閱 [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="135a7-109">For more information about the COLLECTION keyword, see [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="135a7-110">範例</span><span class="sxs-lookup"><span data-stu-id="135a7-110">Example</span></span>  
 <span data-ttu-id="135a7-111">下列範例示範如何使用 COLLECTION 關鍵字將十進位的集合宣告為內嵌查詢函式的引數。</span><span class="sxs-lookup"><span data-stu-id="135a7-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="135a7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="135a7-112">See also</span></span>
- [<span data-ttu-id="135a7-113">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="135a7-113">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
