---
title: marshalCleanupError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6784848a5103dc9206267fc25fe7457257624cb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392027"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="c302f-102">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="c302f-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="c302f-103">如果通用語言執行平台 (CLR) 在嘗試清除用來封送處理本機與 Managed 程式碼界限間之資料類型的暫存結構和記憶體時，發生錯誤，就會啟用 `marshalCleanupError` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="c302f-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c302f-104">徵兆</span><span class="sxs-lookup"><span data-stu-id="c302f-104">Symptoms</span></span>  
 <span data-ttu-id="c302f-105">進行本機與 Managed 程式碼轉換時發生記憶體流失、執行緒文化特性之類的執行階段狀態未還原，或是 <xref:System.Runtime.InteropServices.SafeHandle> 清除發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c302f-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c302f-106">原因</span><span class="sxs-lookup"><span data-stu-id="c302f-106">Cause</span></span>  
 <span data-ttu-id="c302f-107">清除暫存結構時，發生非預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c302f-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c302f-108">解決方式</span><span class="sxs-lookup"><span data-stu-id="c302f-108">Resolution</span></span>  
 <span data-ttu-id="c302f-109">檢閱所有 <xref:System.Runtime.InteropServices.SafeHandle> 建構函式、完成項和自訂封送處理器實作是否有錯誤。</span><span class="sxs-lookup"><span data-stu-id="c302f-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c302f-110">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="c302f-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="c302f-111">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="c302f-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c302f-112">輸出</span><span class="sxs-lookup"><span data-stu-id="c302f-112">Output</span></span>  
 <span data-ttu-id="c302f-113">出現一則訊息，提報在清除期間失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="c302f-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="c302f-114">組態</span><span class="sxs-lookup"><span data-stu-id="c302f-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c302f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c302f-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="c302f-116">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="c302f-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="c302f-117">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="c302f-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
