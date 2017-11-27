---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2624a5dcd2179f35567d19e33e4f981c5d049063
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="4149c-102">ICorDebugHeapValue3::GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="4149c-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="4149c-103">提供與監視鎖定相關事件的執行緒已排入佇列的已排序的清單。</span><span class="sxs-lookup"><span data-stu-id="4149c-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4149c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4149c-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4149c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4149c-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="4149c-106">[out]提供執行緒的已排序的清單 ICorDebugThreadEnum 列舉值。</span><span class="sxs-lookup"><span data-stu-id="4149c-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4149c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="4149c-107">Return Value</span></span>  
 <span data-ttu-id="4149c-108">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="4149c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4149c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4149c-109">HRESULT</span></span>|<span data-ttu-id="4149c-110">描述</span><span class="sxs-lookup"><span data-stu-id="4149c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4149c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4149c-111">S_OK</span></span>|<span data-ttu-id="4149c-112">list 不是空的。</span><span class="sxs-lookup"><span data-stu-id="4149c-112">The list is not empty.</span></span>|  
|<span data-ttu-id="4149c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4149c-113">S_FALSE</span></span>|<span data-ttu-id="4149c-114">清單是空的。</span><span class="sxs-lookup"><span data-stu-id="4149c-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="4149c-115">例外狀況</span><span class="sxs-lookup"><span data-stu-id="4149c-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4149c-116">備註</span><span class="sxs-lookup"><span data-stu-id="4149c-116">Remarks</span></span>  
 <span data-ttu-id="4149c-117">在清單中的第一個執行緒已發行的下一個呼叫的第一個執行緒<xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4149c-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4149c-118">在清單中的下一個執行緒會在下列的呼叫，等發行。</span><span class="sxs-lookup"><span data-stu-id="4149c-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="4149c-119">如果清單不是空的則這個方法會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4149c-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="4149c-120">如果清單是空的方法會傳回 S_FALSE。在此情況下，列舉型別是仍然有效，雖然它是空白。</span><span class="sxs-lookup"><span data-stu-id="4149c-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="4149c-121">在任一情況下，列舉介面是使用僅針對目前已同步處理狀態的持續時間。</span><span class="sxs-lookup"><span data-stu-id="4149c-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="4149c-122">不過，從它在分配的執行緒的介面都有效，直到執行緒結束為止。</span><span class="sxs-lookup"><span data-stu-id="4149c-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="4149c-123">如果`ppThreadEnum`不是有效的指標，結果會是未定義。</span><span class="sxs-lookup"><span data-stu-id="4149c-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="4149c-124">如果發生錯誤，無法判斷，如果有的話，執行緒等候的監視，方法會傳回指出失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="4149c-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4149c-125">需求</span><span class="sxs-lookup"><span data-stu-id="4149c-125">Requirements</span></span>  
 <span data-ttu-id="4149c-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4149c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4149c-127">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4149c-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4149c-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4149c-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4149c-129">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4149c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4149c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4149c-130">See Also</span></span>  
 [<span data-ttu-id="4149c-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4149c-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4149c-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="4149c-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
