---
title: marshalCleanupError MDA
description: 檢查 marshalCleanupError managed 偵錯工具 (MDA) ，因為清除暫存結構時發生未預期的錯誤，所以會叫用此功能。
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
ms.openlocfilehash: e65136f022caa7b1e18a27f7b97a4ef4c27f42d3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271184"
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="4cf8d-103">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="4cf8d-103">marshalCleanupError MDA</span></span>

<span data-ttu-id="4cf8d-104">如果通用語言執行平台 (CLR) 在嘗試清除用來封送處理本機與 Managed 程式碼界限間之資料類型的暫存結構和記憶體時，發生錯誤，就會啟用 `marshalCleanupError` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="4cf8d-104">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="4cf8d-105">徵狀</span><span class="sxs-lookup"><span data-stu-id="4cf8d-105">Symptoms</span></span>  

 <span data-ttu-id="4cf8d-106">進行本機與 Managed 程式碼轉換時發生記憶體流失、執行緒文化特性之類的執行階段狀態未還原，或是 <xref:System.Runtime.InteropServices.SafeHandle> 清除發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cf8d-106">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="4cf8d-107">原因</span><span class="sxs-lookup"><span data-stu-id="4cf8d-107">Cause</span></span>  

 <span data-ttu-id="4cf8d-108">清除暫存結構時，發生非預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cf8d-108">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="4cf8d-109">解決方法</span><span class="sxs-lookup"><span data-stu-id="4cf8d-109">Resolution</span></span>  

 <span data-ttu-id="4cf8d-110">檢閱所有 <xref:System.Runtime.InteropServices.SafeHandle> 建構函式、完成項和自訂封送處理器實作是否有錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cf8d-110">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="4cf8d-111">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="4cf8d-111">Effect on the Runtime</span></span>  

 <span data-ttu-id="4cf8d-112">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="4cf8d-112">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="4cf8d-113">輸出</span><span class="sxs-lookup"><span data-stu-id="4cf8d-113">Output</span></span>  

 <span data-ttu-id="4cf8d-114">出現一則訊息，提報在清除期間失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="4cf8d-114">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="4cf8d-115">設定</span><span class="sxs-lookup"><span data-stu-id="4cf8d-115">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4cf8d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cf8d-116">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="4cf8d-117">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="4cf8d-117">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="4cf8d-118">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="4cf8d-118">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
