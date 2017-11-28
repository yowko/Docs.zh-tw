---
title: "_EFN_StackTrace 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_StackTrace
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_StackTrace
helpviewer_keywords: _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 031812b2c286c5647afb9c88882f22e2c7c3addf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="2871b-102">_EFN_StackTrace 函式</span><span class="sxs-lookup"><span data-stu-id="2871b-102">_EFN_StackTrace Function</span></span>
<span data-ttu-id="2871b-103">提供 Managed 堆疊追蹤以及 `CONTEXT` 記錄之陣列的文字表示，再各提供一個文字表示給 Unmanaged 和 Managed 程式碼之間的每個轉換。</span><span class="sxs-lookup"><span data-stu-id="2871b-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2871b-104">語法</span><span class="sxs-lookup"><span data-stu-id="2871b-104">Syntax</span></span>  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2871b-105">參數</span><span class="sxs-lookup"><span data-stu-id="2871b-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="2871b-106">[in]用戶端進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="2871b-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="2871b-107">[out]堆疊追蹤的文字表示。</span><span class="sxs-lookup"><span data-stu-id="2871b-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="2871b-108">[out]中的字元數的指標`wszTextOut`。</span><span class="sxs-lookup"><span data-stu-id="2871b-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="2871b-109">[out]切換內容的陣列。</span><span class="sxs-lookup"><span data-stu-id="2871b-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="2871b-110">[out]陣列中的轉換內容數目指標。</span><span class="sxs-lookup"><span data-stu-id="2871b-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="2871b-111">[in]內容結構的大小。</span><span class="sxs-lookup"><span data-stu-id="2871b-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="2871b-112">[in]若要顯示的 ebp 暫存器和 enter 堆疊指標 (ESP) 中的前面每個設定為 0 或 SOS_STACKTRACE_SHOWADDRESSES (0x01)`module!functionname`列。</span><span class="sxs-lookup"><span data-stu-id="2871b-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2871b-113">備註</span><span class="sxs-lookup"><span data-stu-id="2871b-113">Remarks</span></span>  
 <span data-ttu-id="2871b-114">`_EFN_StackTrace`結構可以呼叫從 WinDbg 程式設計介面。</span><span class="sxs-lookup"><span data-stu-id="2871b-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="2871b-115">使用參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2871b-115">Parameters are used as follows:</span></span>  
  
-   <span data-ttu-id="2871b-116">如果`wszTextOut`為 null 和`puiTextLength`是不是 null，則函數會傳回的字串長度`puiTextLength`。</span><span class="sxs-lookup"><span data-stu-id="2871b-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
-   <span data-ttu-id="2871b-117">如果`wszTextOut`是不是 null，函式將文字儲存在`wszTextOut`最多所指示位置`puiTextLength`。</span><span class="sxs-lookup"><span data-stu-id="2871b-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="2871b-118">它會傳回成功有沒有足夠的空間中的緩衝區或傳回 E_OUTOFMEMORY 如果緩衝區不夠長。</span><span class="sxs-lookup"><span data-stu-id="2871b-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
-   <span data-ttu-id="2871b-119">如果函式的轉換部分則會忽略`pTransitionContexts`和`puiTransitionContextCount`都是 null。</span><span class="sxs-lookup"><span data-stu-id="2871b-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="2871b-120">在此情況下，函式提供函數名稱的文字輸出的呼叫的端。</span><span class="sxs-lookup"><span data-stu-id="2871b-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
-   <span data-ttu-id="2871b-121">如果`pTransitionContexts`為 null 和`puiTransitionContextCount`是不是 null，此函數會傳回所需內容的項目數`puiTransitionContextCount`。</span><span class="sxs-lookup"><span data-stu-id="2871b-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
-   <span data-ttu-id="2871b-122">如果`pTransitionContexts`是不是 null，函式會將它視為一個陣列的長度為結構`puiTransitionContextCount`。</span><span class="sxs-lookup"><span data-stu-id="2871b-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="2871b-123">結構大小由提供`uiSizeOfContext`，而且必須是大小[SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)或`CONTEXT`架構。</span><span class="sxs-lookup"><span data-stu-id="2871b-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
-   <span data-ttu-id="2871b-124">`wszTextOut`採用下列格式：</span><span class="sxs-lookup"><span data-stu-id="2871b-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   <span data-ttu-id="2871b-125">如果 0x0 十六進位的位移，不會寫入位移。</span><span class="sxs-lookup"><span data-stu-id="2871b-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
-   <span data-ttu-id="2871b-126">如果沒有任何 managed 程式碼的執行緒上目前內容中，函數會傳回 SOS_E_NOMANAGEDCODE。</span><span class="sxs-lookup"><span data-stu-id="2871b-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
-   <span data-ttu-id="2871b-127">`Flags`參數是 0 或若要查看 EBP 及 ESP 前面每個 SOS_STACKTRACE_SHOWADDRESSES`module!functionname`列。</span><span class="sxs-lookup"><span data-stu-id="2871b-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="2871b-128">根據預設，它可以是 0。</span><span class="sxs-lookup"><span data-stu-id="2871b-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="2871b-129">需求</span><span class="sxs-lookup"><span data-stu-id="2871b-129">Requirements</span></span>  
 <span data-ttu-id="2871b-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2871b-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2871b-131">**標頭：** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="2871b-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="2871b-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2871b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2871b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2871b-133">See Also</span></span>  
 [<span data-ttu-id="2871b-134">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="2871b-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
