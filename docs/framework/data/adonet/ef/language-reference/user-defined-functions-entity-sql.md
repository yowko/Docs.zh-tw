---
title: 使用者定義函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 4922e7fada676a6c26042236ccdb6315d6d455ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104620"
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="5d71f-102">使用者定義函式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5d71f-102">User-Defined Functions (Entity SQL)</span></span>
<span data-ttu-id="5d71f-103">Entity SQL 支援呼叫查詢中的使用者定義函式。</span><span class="sxs-lookup"><span data-stu-id="5d71f-103">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="5d71f-104">您可以定義這些函式內嵌在查詢 (請參閱[How to:呼叫使用者定義函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) 或做為概念模型的一部分 (請參閱[How to:概念模型中定義自訂函式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)))。</span><span class="sxs-lookup"><span data-stu-id="5d71f-104">You can define these functions inline with the query (see [How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))).</span></span> <span data-ttu-id="5d71f-105">概念模型函式會定義為 Entity SQL 命令中[DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl)項目[函式](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl)概念模型中的項目。</span><span class="sxs-lookup"><span data-stu-id="5d71f-105">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) element of a [Function](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="5d71f-106">Entity SQL 可讓您定義查詢命令自身中的函式。</span><span class="sxs-lookup"><span data-stu-id="5d71f-106">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="5d71f-107">[函式](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)運算子定義內嵌函式。</span><span class="sxs-lookup"><span data-stu-id="5d71f-107">The [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="5d71f-108">您可以在單一命令中定義多個函式，只要函式的簽章是唯一的，這些函式可以有相同的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="5d71f-108">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="5d71f-109">如需詳細資訊，請參閱 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="5d71f-109">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d71f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d71f-110">See also</span></span>

- [<span data-ttu-id="5d71f-111">函式</span><span class="sxs-lookup"><span data-stu-id="5d71f-111">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
