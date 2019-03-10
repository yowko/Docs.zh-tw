---
title: WF 中的錯誤處理活動
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 410c481745cc62a55a2b6e840d82b01fcc7f5766
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707673"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="007c5-102">WF 中的錯誤處理活動</span><span class="sxs-lookup"><span data-stu-id="007c5-102">Error Handling Activities in WF</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="007c5-103">提供數種系統提供的活動，可用於實作錯誤處理與復原。</span><span class="sxs-lookup"><span data-stu-id="007c5-103">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="007c5-104">如需詳細資訊，請參閱 [例外狀況](exceptions.md)中定義的介面的私用 C++ 專屬實作。</span><span class="sxs-lookup"><span data-stu-id="007c5-104">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="007c5-105">錯誤處理活動</span><span class="sxs-lookup"><span data-stu-id="007c5-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="007c5-106">重新擲回從 `TryCatch` 活動中上次擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="007c5-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="007c5-107">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="007c5-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="007c5-108">實作例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="007c5-108">Implements exception handling.</span></span>|
