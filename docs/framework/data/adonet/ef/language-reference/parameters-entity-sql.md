---
title: "參數 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bb631a752bfe0e741b654ec6774a14c82c89157c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="1f9c2-102">參數 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1f9c2-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="1f9c2-103">參數是定義在 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 外部的變數，通常是透過主應用程式語言使用的繫結 API 來定義。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="1f9c2-104">每一個參數都有一個名稱和型別，</span><span class="sxs-lookup"><span data-stu-id="1f9c2-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="1f9c2-105">使用查詢運算式中所定義的參數名稱在 (@) 符號做為前置詞。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="1f9c2-106">這樣可讓它們避免與屬性名稱或查詢內定義的其他名稱混淆。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="1f9c2-107">主應用程式語言的繫結 API 會提供用來繫結參數的 API。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f9c2-108">範例</span><span class="sxs-lookup"><span data-stu-id="1f9c2-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f9c2-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="1f9c2-109">See Also</span></span>  
 [<span data-ttu-id="1f9c2-110">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="1f9c2-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="1f9c2-111">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="1f9c2-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
