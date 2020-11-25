---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: fef0902aedbcd8572d2dc67fae7927f754af4489
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723307"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="86b35-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法</span><span class="sxs-lookup"><span data-stu-id="86b35-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>

<span data-ttu-id="86b35-103">傳回在這個物件上擁有監視器鎖定的 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="86b35-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b35-104">語法</span><span class="sxs-lookup"><span data-stu-id="86b35-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86b35-105">參數</span><span class="sxs-lookup"><span data-stu-id="86b35-105">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="86b35-106">擴展擁有此物件之監視器鎖定的 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="86b35-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="86b35-107">擴展這個執行緒在回到無人擁有之前，必須釋放鎖定的次數。</span><span class="sxs-lookup"><span data-stu-id="86b35-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86b35-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="86b35-108">Return Value</span></span>  

 <span data-ttu-id="86b35-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="86b35-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="86b35-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86b35-110">HRESULT</span></span>|<span data-ttu-id="86b35-111">描述</span><span class="sxs-lookup"><span data-stu-id="86b35-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86b35-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="86b35-112">S_OK</span></span>|<span data-ttu-id="86b35-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="86b35-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="86b35-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="86b35-114">S_FALSE</span></span>|<span data-ttu-id="86b35-115">沒有 managed 執行緒擁有此物件的監視器鎖定。</span><span class="sxs-lookup"><span data-stu-id="86b35-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="86b35-116">例外</span><span class="sxs-lookup"><span data-stu-id="86b35-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86b35-117">備註</span><span class="sxs-lookup"><span data-stu-id="86b35-117">Remarks</span></span>  

 <span data-ttu-id="86b35-118">如果 managed 執行緒擁有此物件的監視器鎖定：</span><span class="sxs-lookup"><span data-stu-id="86b35-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="86b35-119">方法會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="86b35-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="86b35-120">執行緒物件會一直有效，直到執行緒結束為止。</span><span class="sxs-lookup"><span data-stu-id="86b35-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="86b35-121">如果沒有 managed 執行緒擁有此物件的監視器鎖定，而且沒有變更 `ppThread` `pAcquisitionCount` ，則方法會傳回 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="86b35-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="86b35-122">如果 `ppThread` 或不是 `pAcquisitionCount` 有效的指標，則結果為未定義。</span><span class="sxs-lookup"><span data-stu-id="86b35-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="86b35-123">如果發生錯誤，導致無法判斷線程（如果有的話）擁有此物件的監視器鎖定，方法會傳回指出失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="86b35-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86b35-124">需求</span><span class="sxs-lookup"><span data-stu-id="86b35-124">Requirements</span></span>  

 <span data-ttu-id="86b35-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86b35-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86b35-126">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86b35-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86b35-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86b35-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86b35-128">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86b35-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b35-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86b35-129">See also</span></span>

- [<span data-ttu-id="86b35-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="86b35-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="86b35-131">偵錯</span><span class="sxs-lookup"><span data-stu-id="86b35-131">Debugging</span></span>](index.md)
