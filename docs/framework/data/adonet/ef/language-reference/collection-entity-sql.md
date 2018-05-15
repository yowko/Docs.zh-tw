---
title: COLLECTION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 03228bfa-be3a-4ccc-82f8-eee429f85cf1
ms.openlocfilehash: 2b13d373e6c54221249b17de4fa91347cbc0f9e6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="collection-entity-sql"></a><span data-ttu-id="27281-102">COLLECTION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="27281-102">COLLECTION (Entity SQL)</span></span>
<span data-ttu-id="27281-103">COLLECTION 關鍵字只用於內嵌函式的定義。</span><span class="sxs-lookup"><span data-stu-id="27281-103">The COLLECTION keyword is only used in the definition of an inline function.</span></span> <span data-ttu-id="27281-104">集合函式是處理值的集合並產生純量輸出的函式。</span><span class="sxs-lookup"><span data-stu-id="27281-104">Collection functions are functions that operate on a collection of values and produce a scalar output.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27281-105">語法</span><span class="sxs-lookup"><span data-stu-id="27281-105">Syntax</span></span>  
  
```  
COLLECTION(type_definition)   
```  
  
## <a name="arguments"></a><span data-ttu-id="27281-106">引數</span><span class="sxs-lookup"><span data-stu-id="27281-106">Arguments</span></span>  
 `type_definition`  
 <span data-ttu-id="27281-107">傳回支援的型別、資料列或參考等集合的運算式。</span><span class="sxs-lookup"><span data-stu-id="27281-107">An expression that returns a collection of supported types, rows, or references.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27281-108">備註</span><span class="sxs-lookup"><span data-stu-id="27281-108">Remarks</span></span>  
 <span data-ttu-id="27281-109">如需 COLLECTION 關鍵字的詳細資訊，請參閱 [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="27281-109">For more information about the COLLECTION keyword, see [Type Definitions](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27281-110">範例</span><span class="sxs-lookup"><span data-stu-id="27281-110">Example</span></span>  
 <span data-ttu-id="27281-111">下列範例示範如何使用 COLLECTION 關鍵字將十進位的集合宣告為內嵌查詢函式的引數。</span><span class="sxs-lookup"><span data-stu-id="27281-111">The following sample shows how to use the COLLECTION keyword to declare a collection of decimals as an argument for an inline query function.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#Collection_GroupPartition](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#collection_grouppartition)]  
  
## <a name="see-also"></a><span data-ttu-id="27281-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27281-112">See Also</span></span>  
 [<span data-ttu-id="27281-113">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="27281-113">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
