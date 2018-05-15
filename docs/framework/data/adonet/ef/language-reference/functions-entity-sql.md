---
title: 函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: 6c8a44a4e347ffabd665847f02bfafe267a14103
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="functions-entity-sql"></a><span data-ttu-id="11f01-102">函式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="11f01-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="11f01-103">Entity SQL 支援使用者定義函式、標準函式及提供者特有的函式。</span><span class="sxs-lookup"><span data-stu-id="11f01-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="11f01-104">使用者定義函式可在概念模型中指定，或是內嵌於查詢之中。</span><span class="sxs-lookup"><span data-stu-id="11f01-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="11f01-105">如需詳細資訊，請參閱[使用者定義函數](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="11f01-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="11f01-106">標準函式會預先定義在 Entity Framework 中，而且應該受到資料提供者的支援。</span><span class="sxs-lookup"><span data-stu-id="11f01-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="11f01-107">如果使用者呼叫的函式未受到提供者的支援，Entity SQL 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="11f01-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="11f01-108">因此，通常建議優先使用標準函式勝於存放區特有的函式，後者位於提供者特有的命名空間內。</span><span class="sxs-lookup"><span data-stu-id="11f01-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="11f01-109">如需詳細資訊，請參閱[標準函式](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="11f01-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="11f01-110">Microsoft SQL Client Managed Provider 提供了一組提供者特有的函式。</span><span class="sxs-lookup"><span data-stu-id="11f01-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="11f01-111">如需詳細資訊，請參閱[適用於 Entity Framework 函式的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="11f01-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11f01-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="11f01-112">In This Section</span></span>  
 [<span data-ttu-id="11f01-113">使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="11f01-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="11f01-114">函式多載解析</span><span class="sxs-lookup"><span data-stu-id="11f01-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="11f01-115">彙總函式</span><span class="sxs-lookup"><span data-stu-id="11f01-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="11f01-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11f01-116">See Also</span></span>  
 [<span data-ttu-id="11f01-117">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="11f01-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
