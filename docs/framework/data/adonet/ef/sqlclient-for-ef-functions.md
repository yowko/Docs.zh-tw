---
title: "適用於 Entity Framework 的 SqlClient 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71a3613c-b94e-494c-8ad8-90cf86ae0b87
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08526aeebd01196c064154a35df267b8040df796
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sqlclient-for-entity-framework-functions"></a><span data-ttu-id="e8380-102">適用於 Entity Framework 的 SqlClient 函式</span><span class="sxs-lookup"><span data-stu-id="e8380-102">SqlClient for Entity Framework Functions</span></span>
<span data-ttu-id="e8380-103">適用於 Entity Framework 的 .NET Framework Data Provider for SQL Server (SqlClient) 提供了一組可執行數學和彙總 (Aggregation) 計算的函式，以及可執行 `System.DateTime` 和 `string` 作業的函式。</span><span class="sxs-lookup"><span data-stu-id="e8380-103">The .NET Framework Data Provider for SQL Server (SqlClient) for the Entity Framework provides a set of functions to perform mathematical and aggregation calculations, as well as functions to perform `System.DateTime` and `string` operations.</span></span> <span data-ttu-id="e8380-104">這些函式位於 `SQLServer` 命名空間 (Namespace) 中。</span><span class="sxs-lookup"><span data-stu-id="e8380-104">These functions are in the `SQLServer` namespace.</span></span>  
  
 <span data-ttu-id="e8380-105">函式可以使用的任何提供者的清單，請參閱[標準函式](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="e8380-105">For a list of functions that should work with any provider, see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="e8380-106">如需如何標準 SQL Server 函式的函式對應資訊，請參閱[概念模型標準與 SQL Server 函式對應](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="e8380-106">For information about how canonical functions map to SQL Server functions, see [Conceptual Model Canonical to SQL Server Functions Mapping](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8380-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e8380-107">In This Section</span></span>  
 [<span data-ttu-id="e8380-108">概念模型標準與 SQL Server 函式的對應</span><span class="sxs-lookup"><span data-stu-id="e8380-108">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
  
 [<span data-ttu-id="e8380-109">彙總函式</span><span class="sxs-lookup"><span data-stu-id="e8380-109">Aggregate Functions</span></span>](../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
 [<span data-ttu-id="e8380-110">日期和時間函數</span><span class="sxs-lookup"><span data-stu-id="e8380-110">Date and Time Functions</span></span>](../../../../../docs/framework/data/adonet/ef/date-and-time-functions.md)  
  
 [<span data-ttu-id="e8380-111">數學函式</span><span class="sxs-lookup"><span data-stu-id="e8380-111">Mathematical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/mathematical-functions.md)  
  
 [<span data-ttu-id="e8380-112">字串函式</span><span class="sxs-lookup"><span data-stu-id="e8380-112">String Functions</span></span>](../../../../../docs/framework/data/adonet/ef/string-functions.md)  
  
 [<span data-ttu-id="e8380-113">系統函數</span><span class="sxs-lookup"><span data-stu-id="e8380-113">System Functions</span></span>](../../../../../docs/framework/data/adonet/ef/system-functions.md)  
  
## <a name="see-also"></a><span data-ttu-id="e8380-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8380-114">See Also</span></span>  
 [<span data-ttu-id="e8380-115">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="e8380-115">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e8380-116">Entity SQL 概觀</span><span class="sxs-lookup"><span data-stu-id="e8380-116">Entity SQL Overview</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
