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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102787"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="af320-102">ICorDebugHeapValue3::GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="af320-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="af320-103">提供的監視器鎖定相關聯的事件的執行緒已排入佇列的已排序的清單。</span><span class="sxs-lookup"><span data-stu-id="af320-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af320-104">語法</span><span class="sxs-lookup"><span data-stu-id="af320-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af320-105">參數</span><span class="sxs-lookup"><span data-stu-id="af320-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="af320-106">[out]ICorDebugThreadEnum 列舉程式，可用的執行緒已排序的清單。</span><span class="sxs-lookup"><span data-stu-id="af320-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af320-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="af320-107">Return Value</span></span>  
 <span data-ttu-id="af320-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="af320-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="af320-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af320-109">HRESULT</span></span>|<span data-ttu-id="af320-110">描述</span><span class="sxs-lookup"><span data-stu-id="af320-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af320-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="af320-111">S_OK</span></span>|<span data-ttu-id="af320-112">list 不是空的。</span><span class="sxs-lookup"><span data-stu-id="af320-112">The list is not empty.</span></span>|  
|<span data-ttu-id="af320-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="af320-113">S_FALSE</span></span>|<span data-ttu-id="af320-114">清單是空的。</span><span class="sxs-lookup"><span data-stu-id="af320-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="af320-115">例外狀況</span><span class="sxs-lookup"><span data-stu-id="af320-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af320-116">備註</span><span class="sxs-lookup"><span data-stu-id="af320-116">Remarks</span></span>  
 <span data-ttu-id="af320-117">在清單中的第一個執行緒已發行的下一個呼叫的第一個執行緒<xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="af320-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="af320-118">在清單中的下一個執行緒已發行下列呼叫，等等。</span><span class="sxs-lookup"><span data-stu-id="af320-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="af320-119">如果清單不是空的則這個方法會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="af320-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="af320-120">如果清單是空的則方法會傳回 S_FALSE。在此情況下，列舉型別是仍然有效，雖然是空的。</span><span class="sxs-lookup"><span data-stu-id="af320-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="af320-121">在任一情況下，列舉型別介面是可使用僅針對目前的同步處理狀態的持續時間。</span><span class="sxs-lookup"><span data-stu-id="af320-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="af320-122">不過，執行緒的介面從中鈔票都有效，直到執行緒結束為止。</span><span class="sxs-lookup"><span data-stu-id="af320-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="af320-123">如果`ppThreadEnum`不是有效的指標，結果為未定義。</span><span class="sxs-lookup"><span data-stu-id="af320-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="af320-124">如果發生錯誤，它無法判別，如果有的話，執行緒等候的監視器，則這個方法會傳回指出失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="af320-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af320-125">需求</span><span class="sxs-lookup"><span data-stu-id="af320-125">Requirements</span></span>  
 <span data-ttu-id="af320-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af320-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af320-127">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af320-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af320-128">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af320-128">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="af320-129">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="af320-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af320-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af320-130">See also</span></span>

- [<span data-ttu-id="af320-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="af320-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="af320-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="af320-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
