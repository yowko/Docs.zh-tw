---
title: "使用者定義函式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b97834a500328f7853b8a361ec20d7ff06eda3d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="f21d9-102">使用者定義函式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f21d9-102">User-Defined Functions (Entity SQL)</span></span>
<span data-ttu-id="f21d9-103">Entity SQL 支援呼叫查詢中的使用者定義函式。</span><span class="sxs-lookup"><span data-stu-id="f21d9-103">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="f21d9-104">您可以定義這些函式的內嵌查詢 (請參閱[How to: Call a User-Defined Function](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) 或做為概念模型的一部分 (請參閱[如何： 定義概念模型中的自訂函式](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f))。</span><span class="sxs-lookup"><span data-stu-id="f21d9-104">You can define these functions inline with the query (see [How to: Call a User-Defined Function](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)).</span></span> <span data-ttu-id="f21d9-105">概念模型函式定義在 Entity SQL 命令為[DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e)元素[函式](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134)概念模型中的項目。</span><span class="sxs-lookup"><span data-stu-id="f21d9-105">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) element of a [Function](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="f21d9-106">Entity SQL 可讓您定義查詢命令自身中的函式。</span><span class="sxs-lookup"><span data-stu-id="f21d9-106">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="f21d9-107">[函式](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)運算子定義內嵌函式。</span><span class="sxs-lookup"><span data-stu-id="f21d9-107">The [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="f21d9-108">您可以在單一命令中定義多個函式，只要函式的簽章是唯一的，這些函式可以有相同的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="f21d9-108">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="f21d9-109">如需詳細資訊，請參閱 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="f21d9-109">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f21d9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f21d9-110">See Also</span></span>  
 [<span data-ttu-id="f21d9-111">函式</span><span class="sxs-lookup"><span data-stu-id="f21d9-111">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
