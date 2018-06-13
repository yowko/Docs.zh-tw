---
title: WF 中的錯誤處理活動
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 51431e367f0ec8874588a52cb4dbd76d714768fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512381"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="af6d5-102">WF 中的錯誤處理活動</span><span class="sxs-lookup"><span data-stu-id="af6d5-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="af6d5-103"> 提供數種系統提供的活動，可用於實作錯誤處理與復原。</span><span class="sxs-lookup"><span data-stu-id="af6d5-103"> provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="af6d5-104">如需詳細資訊，請參閱[例外狀況](../../../docs/framework/windows-workflow-foundation/exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="af6d5-104">For more information, see [Exceptions](../../../docs/framework/windows-workflow-foundation/exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="af6d5-105">錯誤處理活動</span><span class="sxs-lookup"><span data-stu-id="af6d5-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="af6d5-106">重新擲回從 `TryCatch` 活動中上次擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="af6d5-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="af6d5-107">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="af6d5-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="af6d5-108">實作例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="af6d5-108">Implements exception handling.</span></span>|
