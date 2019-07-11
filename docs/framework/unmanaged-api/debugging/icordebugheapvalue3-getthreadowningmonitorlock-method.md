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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4322a7e23c7085dadb3b2df6c1f72125aa685cef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756612"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="1bef4-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock 方法</span><span class="sxs-lookup"><span data-stu-id="1bef4-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="1bef4-103">傳回擁有此物件的監視器鎖定的 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="1bef4-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bef4-104">語法</span><span class="sxs-lookup"><span data-stu-id="1bef4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bef4-105">參數</span><span class="sxs-lookup"><span data-stu-id="1bef4-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="1bef4-106">[out]擁有此物件的監視器鎖定的 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="1bef4-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="1bef4-107">[out]此執行緒就必須釋放鎖定之前它會返回正在未擁有的次數。</span><span class="sxs-lookup"><span data-stu-id="1bef4-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bef4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1bef4-108">Return Value</span></span>  
 <span data-ttu-id="1bef4-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bef4-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1bef4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bef4-110">HRESULT</span></span>|<span data-ttu-id="1bef4-111">描述</span><span class="sxs-lookup"><span data-stu-id="1bef4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bef4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bef4-112">S_OK</span></span>|<span data-ttu-id="1bef4-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="1bef4-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="1bef4-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1bef4-114">S_FALSE</span></span>|<span data-ttu-id="1bef4-115">沒有任何受管理的執行緒擁有此物件的監視器鎖定。</span><span class="sxs-lookup"><span data-stu-id="1bef4-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1bef4-116">例外狀況</span><span class="sxs-lookup"><span data-stu-id="1bef4-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bef4-117">備註</span><span class="sxs-lookup"><span data-stu-id="1bef4-117">Remarks</span></span>  
 <span data-ttu-id="1bef4-118">如果 managed 的執行緒擁有此物件的監視器鎖定：</span><span class="sxs-lookup"><span data-stu-id="1bef4-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="1bef4-119">方法會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1bef4-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="1bef4-120">執行緒物件是有效的直到執行緒結束為止。</span><span class="sxs-lookup"><span data-stu-id="1bef4-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="1bef4-121">如果沒有任何受管理的執行緒擁有這個物件的監視器鎖定`ppThread`和`pAcquisitionCount`維持不變，而方法會傳回 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="1bef4-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="1bef4-122">如果`ppThread`或`pAcquisitionCount`不是有效的指標，結果為未定義。</span><span class="sxs-lookup"><span data-stu-id="1bef4-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="1bef4-123">如果發生錯誤，無法判斷的如果有的話，執行緒擁有監視器上的鎖定這個物件，這個方法會傳回指出失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="1bef4-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bef4-124">需求</span><span class="sxs-lookup"><span data-stu-id="1bef4-124">Requirements</span></span>  
 <span data-ttu-id="1bef4-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bef4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bef4-126">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bef4-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bef4-127">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bef4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bef4-128">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bef4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bef4-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bef4-129">See also</span></span>

- [<span data-ttu-id="1bef4-130">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1bef4-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1bef4-131">偵錯</span><span class="sxs-lookup"><span data-stu-id="1bef4-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
