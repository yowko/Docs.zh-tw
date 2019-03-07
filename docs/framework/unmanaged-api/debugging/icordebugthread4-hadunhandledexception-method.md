---
title: ICorDebugThread4::HadUnhandledException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ef4049ee8b1a4881128047b4d7e50fd0a28ea31
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499195"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="70b16-102">ICorDebugThread4::HadUnhandledException 方法</span><span class="sxs-lookup"><span data-stu-id="70b16-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="70b16-103">指出是否在執行緒曾經有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="70b16-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70b16-104">語法</span><span class="sxs-lookup"><span data-stu-id="70b16-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="70b16-105">參數</span><span class="sxs-lookup"><span data-stu-id="70b16-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="70b16-106">[out]已排序列舉的位址指標[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="70b16-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70b16-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="70b16-107">Return Value</span></span>  
 <span data-ttu-id="70b16-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="70b16-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="70b16-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70b16-109">HRESULT</span></span>|<span data-ttu-id="70b16-110">描述</span><span class="sxs-lookup"><span data-stu-id="70b16-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70b16-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="70b16-111">S_OK</span></span>|<span data-ttu-id="70b16-112">執行緒已自其建立處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="70b16-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="70b16-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="70b16-113">S_FALSE</span></span>|<span data-ttu-id="70b16-114">執行緒永遠不會發生未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="70b16-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70b16-115">備註</span><span class="sxs-lookup"><span data-stu-id="70b16-115">Remarks</span></span>  
 <span data-ttu-id="70b16-116">這個方法會指出是否在執行緒曾經有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="70b16-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="70b16-117">依時間觸發未處理的例外狀況的回呼，或起始原生的 JIT 附加時，此方法保證會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="70b16-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="70b16-118">不保證可[ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)方法會傳回未處理的例外狀況; 不過，它將如果處理程序已不還繼續執行時或之後取得的未處理的例外狀況的回呼原生 JIT 附加。</span><span class="sxs-lookup"><span data-stu-id="70b16-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="70b16-119">此外，很可能 （雖然不太可能） 有多個執行緒的未處理例外狀況在原生的 JIT 附加，就會觸發的時間。</span><span class="sxs-lookup"><span data-stu-id="70b16-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="70b16-120">在此情況下沒有任何方法來判斷哪一個例外狀況觸發 JIT 附加。</span><span class="sxs-lookup"><span data-stu-id="70b16-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70b16-121">需求</span><span class="sxs-lookup"><span data-stu-id="70b16-121">Requirements</span></span>  
 <span data-ttu-id="70b16-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70b16-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70b16-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70b16-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70b16-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70b16-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70b16-125">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70b16-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b16-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70b16-126">See also</span></span>
- [<span data-ttu-id="70b16-127">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="70b16-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="70b16-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="70b16-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="70b16-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="70b16-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
