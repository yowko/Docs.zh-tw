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
ms.openlocfilehash: 15900fab59d172ada67d8aefeab698e1b44f808e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794396"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="44a9a-102">ICorDebugHeapValue3::GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="44a9a-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="44a9a-103">提供在與監視器鎖定相關聯的事件上排入佇列之執行緒的已排序清單。</span><span class="sxs-lookup"><span data-stu-id="44a9a-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="44a9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44a9a-105">參數</span><span class="sxs-lookup"><span data-stu-id="44a9a-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="44a9a-106">脫銷提供執行緒之已排序清單的 ICorDebugThreadEnum 列舉值。</span><span class="sxs-lookup"><span data-stu-id="44a9a-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44a9a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="44a9a-107">Return Value</span></span>  
 <span data-ttu-id="44a9a-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="44a9a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="44a9a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44a9a-109">HRESULT</span></span>|<span data-ttu-id="44a9a-110">描述</span><span class="sxs-lookup"><span data-stu-id="44a9a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44a9a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="44a9a-111">S_OK</span></span>|<span data-ttu-id="44a9a-112">list 不是空的。</span><span class="sxs-lookup"><span data-stu-id="44a9a-112">The list is not empty.</span></span>|  
|<span data-ttu-id="44a9a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="44a9a-113">S_FALSE</span></span>|<span data-ttu-id="44a9a-114">清單是空的。</span><span class="sxs-lookup"><span data-stu-id="44a9a-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="44a9a-115">例外狀況</span><span class="sxs-lookup"><span data-stu-id="44a9a-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44a9a-116">備註</span><span class="sxs-lookup"><span data-stu-id="44a9a-116">Remarks</span></span>  
 <span data-ttu-id="44a9a-117">清單中的第一個執行緒是 <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>下一次呼叫所釋放的第一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="44a9a-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44a9a-118">清單中的下一個執行緒會在下列呼叫中釋放，依此類推。</span><span class="sxs-lookup"><span data-stu-id="44a9a-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="44a9a-119">如果清單不是空的，這個方法會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="44a9a-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="44a9a-120">如果清單是空的，此方法會傳回 S_FALSE;在此情況下，列舉仍然有效，但它是空的。</span><span class="sxs-lookup"><span data-stu-id="44a9a-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="44a9a-121">在任一情況下，列舉介面僅適用于目前已同步處理狀態的持續時間。</span><span class="sxs-lookup"><span data-stu-id="44a9a-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="44a9a-122">不過，從它所分配的執行緒介面是有效的，直到執行緒結束為止。</span><span class="sxs-lookup"><span data-stu-id="44a9a-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="44a9a-123">如果 `ppThreadEnum` 不是有效的指標，則結果會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="44a9a-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="44a9a-124">如果發生錯誤，因此無法判斷線程是否正在等候監視器，此方法會傳回表示失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="44a9a-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44a9a-125">需求</span><span class="sxs-lookup"><span data-stu-id="44a9a-125">Requirements</span></span>  
 <span data-ttu-id="44a9a-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44a9a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44a9a-127">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44a9a-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44a9a-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44a9a-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44a9a-129">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44a9a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44a9a-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="44a9a-130">See also</span></span>

- [<span data-ttu-id="44a9a-131">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="44a9a-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="44a9a-132">偵錯</span><span class="sxs-lookup"><span data-stu-id="44a9a-132">Debugging</span></span>](index.md)
