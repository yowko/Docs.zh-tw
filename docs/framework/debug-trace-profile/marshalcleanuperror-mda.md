---
title: marshalCleanupError MDA
description: 請檢查 marshalCleanupError managed 偵錯工具（MDA），這是叫用的，因為清除暫存結構時發生未預期的錯誤。
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
ms.openlocfilehash: 3c7498d6f51484de3a2e84d611a2634f53724ab6
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051606"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="72dbe-103">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="72dbe-103">marshalCleanupError MDA</span></span>
<span data-ttu-id="72dbe-104">如果通用語言執行平台 (CLR) 在嘗試清除用來封送處理本機與 Managed 程式碼界限間之資料類型的暫存結構和記憶體時，發生錯誤，就會啟用 `marshalCleanupError` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="72dbe-104">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="72dbe-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="72dbe-105">Symptoms</span></span>  
 <span data-ttu-id="72dbe-106">進行本機與 Managed 程式碼轉換時發生記憶體流失、執行緒文化特性之類的執行階段狀態未還原，或是 <xref:System.Runtime.InteropServices.SafeHandle> 清除發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="72dbe-106">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="72dbe-107">原因</span><span class="sxs-lookup"><span data-stu-id="72dbe-107">Cause</span></span>  
 <span data-ttu-id="72dbe-108">清除暫存結構時，發生非預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="72dbe-108">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="72dbe-109">解決方案</span><span class="sxs-lookup"><span data-stu-id="72dbe-109">Resolution</span></span>  
 <span data-ttu-id="72dbe-110">檢閱所有 <xref:System.Runtime.InteropServices.SafeHandle> 建構函式、完成項和自訂封送處理器實作是否有錯誤。</span><span class="sxs-lookup"><span data-stu-id="72dbe-110">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="72dbe-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="72dbe-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="72dbe-112">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="72dbe-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="72dbe-113">輸出</span><span class="sxs-lookup"><span data-stu-id="72dbe-113">Output</span></span>  
 <span data-ttu-id="72dbe-114">出現一則訊息，提報在清除期間失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="72dbe-114">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="72dbe-115">組態</span><span class="sxs-lookup"><span data-stu-id="72dbe-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72dbe-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72dbe-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="72dbe-117">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="72dbe-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="72dbe-118">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="72dbe-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
