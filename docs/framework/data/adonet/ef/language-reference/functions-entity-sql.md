---
title: 函式 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: bef959ae6a835b5d1d696162528a8f904c59e8e5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201066"
---
# <a name="functions-entity-sql"></a><span data-ttu-id="ce62e-102">函式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce62e-102">Functions (Entity SQL)</span></span>

<span data-ttu-id="ce62e-103">Entity SQL 支援使用者定義函式、標準函式及提供者特有的函式。</span><span class="sxs-lookup"><span data-stu-id="ce62e-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="ce62e-104">使用者定義函式可在概念模型中指定，或是內嵌於查詢之中。</span><span class="sxs-lookup"><span data-stu-id="ce62e-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="ce62e-105">如需詳細資訊，請參閱 [使用者定義函數](user-defined-functions-entity-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ce62e-105">For more information, see [User-Defined Functions](user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="ce62e-106">標準函式會預先定義在 Entity Framework 中，而且應該受到資料提供者的支援。</span><span class="sxs-lookup"><span data-stu-id="ce62e-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="ce62e-107">如果使用者呼叫的函式未受到提供者的支援，Entity SQL 將會失敗。</span><span class="sxs-lookup"><span data-stu-id="ce62e-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="ce62e-108">因此，通常建議優先使用標準函式勝於存放區特有的函式，後者位於提供者特有的命名空間內。</span><span class="sxs-lookup"><span data-stu-id="ce62e-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="ce62e-109">如需詳細資訊，請參閱 [標準](canonical-functions.md)函式。</span><span class="sxs-lookup"><span data-stu-id="ce62e-109">For more information, see [Canonical Functions](canonical-functions.md).</span></span>  
  
 <span data-ttu-id="ce62e-110">Microsoft SQL Client Managed Provider 提供了一組提供者特有的函式。</span><span class="sxs-lookup"><span data-stu-id="ce62e-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="ce62e-111">如需詳細資訊，請參閱 Entity Framework 函式 [的 SqlClient](../sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="ce62e-111">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce62e-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="ce62e-112">In This Section</span></span>  

 [<span data-ttu-id="ce62e-113">使用者定義的函式</span><span class="sxs-lookup"><span data-stu-id="ce62e-113">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="ce62e-114">函式多載解析</span><span class="sxs-lookup"><span data-stu-id="ce62e-114">Function Overload Resolution</span></span>](function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="ce62e-115">彙總函式</span><span class="sxs-lookup"><span data-stu-id="ce62e-115">Aggregate Functions</span></span>](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="ce62e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce62e-116">See also</span></span>

- [<span data-ttu-id="ce62e-117">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="ce62e-117">Entity SQL Overview</span></span>](entity-sql-overview.md)
