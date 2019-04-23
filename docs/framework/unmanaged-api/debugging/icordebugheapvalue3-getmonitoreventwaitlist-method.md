---
title: ICorDebugHeapValue3::GetMonitorEventWaitList 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db331d75244d59aacf2207a6b83a3f337a64b989
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102787"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="ce9f2-102">ICorDebugHeapValue3::GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="ce9f2-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="ce9f2-103">提供的監視器鎖定相關聯的事件的執行緒已排入佇列的已排序的清單。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce9f2-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce9f2-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce9f2-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce9f2-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="ce9f2-106">[out]ICorDebugThreadEnum 列舉程式，可用的執行緒已排序的清單。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce9f2-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ce9f2-107">Return Value</span></span>  
 <span data-ttu-id="ce9f2-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ce9f2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce9f2-109">HRESULT</span></span>|<span data-ttu-id="ce9f2-110">描述</span><span class="sxs-lookup"><span data-stu-id="ce9f2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce9f2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce9f2-111">S_OK</span></span>|<span data-ttu-id="ce9f2-112">list 不是空的。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-112">The list is not empty.</span></span>|  
|<span data-ttu-id="ce9f2-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ce9f2-113">S_FALSE</span></span>|<span data-ttu-id="ce9f2-114">清單是空的。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ce9f2-115">例外狀況</span><span class="sxs-lookup"><span data-stu-id="ce9f2-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce9f2-116">備註</span><span class="sxs-lookup"><span data-stu-id="ce9f2-116">Remarks</span></span>  
 <span data-ttu-id="ce9f2-117">在清單中的第一個執行緒已發行的下一個呼叫的第一個執行緒<xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ce9f2-118">在清單中的下一個執行緒已發行下列呼叫，等等。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="ce9f2-119">如果清單不是空的則這個方法會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="ce9f2-120">如果清單是空的則方法會傳回 S_FALSE。在此情況下，列舉型別是仍然有效，雖然是空的。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="ce9f2-121">在任一情況下，列舉型別介面是可使用僅針對目前的同步處理狀態的持續時間。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="ce9f2-122">不過，執行緒的介面從中鈔票都有效，直到執行緒結束為止。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="ce9f2-123">如果`ppThreadEnum`不是有效的指標，結果為未定義。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="ce9f2-124">如果發生錯誤，它無法判別，如果有的話，執行緒等候的監視器，則這個方法會傳回指出失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9f2-125">需求</span><span class="sxs-lookup"><span data-stu-id="ce9f2-125">Requirements</span></span>  
 <span data-ttu-id="ce9f2-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce9f2-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9f2-127">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce9f2-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce9f2-128">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce9f2-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce9f2-129">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9f2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9f2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce9f2-130">See also</span></span>

- [<span data-ttu-id="ce9f2-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ce9f2-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ce9f2-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="ce9f2-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
