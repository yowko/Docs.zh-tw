---
title: 參數 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: e1bb633f7f7c7908a5f424991f20a5cd89aee5aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150010"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="fdf32-102">參數 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fdf32-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="fdf32-103">參數是定義在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 外部的變數，通常是透過主應用程式語言使用的繫結 API 來定義。</span><span class="sxs-lookup"><span data-stu-id="fdf32-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="fdf32-104">每一個參數都有一個名稱和型別，</span><span class="sxs-lookup"><span data-stu-id="fdf32-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="fdf32-105">參數名稱定義在查詢運算式內，使用 At (@) 符號當做前置詞。</span><span class="sxs-lookup"><span data-stu-id="fdf32-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="fdf32-106">這樣可讓它們避免與屬性名稱或查詢內定義的其他名稱混淆。</span><span class="sxs-lookup"><span data-stu-id="fdf32-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="fdf32-107">主應用程式語言的繫結 API 會提供用來繫結參數的 API。</span><span class="sxs-lookup"><span data-stu-id="fdf32-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdf32-108">範例</span><span class="sxs-lookup"><span data-stu-id="fdf32-108">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="fdf32-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdf32-109">See also</span></span>

- [<span data-ttu-id="fdf32-110">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="fdf32-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fdf32-111">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="fdf32-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
