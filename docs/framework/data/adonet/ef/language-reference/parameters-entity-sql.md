---
title: 參數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 47a1514933904daa623adc151d50525f011e07a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187666"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="a6ca0-102">參數 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a6ca0-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="a6ca0-103">參數是定義在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 外部的變數，通常是透過主應用程式語言使用的繫結 API 來定義。</span><span class="sxs-lookup"><span data-stu-id="a6ca0-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="a6ca0-104">每一個參數都有一個名稱和型別，</span><span class="sxs-lookup"><span data-stu-id="a6ca0-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="a6ca0-105">參數名稱會定義在查詢運算式中使用在 (@) 符號當做前置詞。</span><span class="sxs-lookup"><span data-stu-id="a6ca0-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="a6ca0-106">這樣可讓它們避免與屬性名稱或查詢內定義的其他名稱混淆。</span><span class="sxs-lookup"><span data-stu-id="a6ca0-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="a6ca0-107">主應用程式語言的繫結 API 會提供用來繫結參數的 API。</span><span class="sxs-lookup"><span data-stu-id="a6ca0-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6ca0-108">範例</span><span class="sxs-lookup"><span data-stu-id="a6ca0-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6ca0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6ca0-109">See also</span></span>

- [<span data-ttu-id="a6ca0-110">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="a6ca0-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="a6ca0-111">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="a6ca0-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
