---
title: 參數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: c8bdb54e52b4c0d189f3bff72bdb24785c1a9c27
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="0b174-102">參數 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0b174-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="0b174-103">參數是定義在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 外部的變數，通常是透過主應用程式語言使用的繫結 API 來定義。</span><span class="sxs-lookup"><span data-stu-id="0b174-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="0b174-104">每一個參數都有一個名稱和型別，</span><span class="sxs-lookup"><span data-stu-id="0b174-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="0b174-105">使用查詢運算式中所定義的參數名稱在 (@) 符號做為前置詞。</span><span class="sxs-lookup"><span data-stu-id="0b174-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="0b174-106">這樣可讓它們避免與屬性名稱或查詢內定義的其他名稱混淆。</span><span class="sxs-lookup"><span data-stu-id="0b174-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="0b174-107">主應用程式語言的繫結 API 會提供用來繫結參數的 API。</span><span class="sxs-lookup"><span data-stu-id="0b174-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b174-108">範例</span><span class="sxs-lookup"><span data-stu-id="0b174-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b174-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b174-109">See Also</span></span>  
 [<span data-ttu-id="0b174-110">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="0b174-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="0b174-111">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="0b174-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
