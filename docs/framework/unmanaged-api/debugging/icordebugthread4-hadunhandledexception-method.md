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
ms.openlocfilehash: f558a4c94afeb69f58605958ddcb91e4be772c39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791342"
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="ca24d-102">ICorDebugThread4::HadUnhandledException 方法</span><span class="sxs-lookup"><span data-stu-id="ca24d-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="ca24d-103">指出執行緒是否曾經有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca24d-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca24d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca24d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca24d-105">參數</span><span class="sxs-lookup"><span data-stu-id="ca24d-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="ca24d-106">脫銷[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構的已排序列舉之位址的指標。</span><span class="sxs-lookup"><span data-stu-id="ca24d-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca24d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ca24d-107">Return Value</span></span>  
 <span data-ttu-id="ca24d-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca24d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ca24d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ca24d-109">HRESULT</span></span>|<span data-ttu-id="ca24d-110">描述</span><span class="sxs-lookup"><span data-stu-id="ca24d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ca24d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca24d-111">S_OK</span></span>|<span data-ttu-id="ca24d-112">執行緒在建立之後有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca24d-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="ca24d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ca24d-113">S_FALSE</span></span>|<span data-ttu-id="ca24d-114">執行緒從未發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca24d-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca24d-115">備註</span><span class="sxs-lookup"><span data-stu-id="ca24d-115">Remarks</span></span>  
 <span data-ttu-id="ca24d-116">這個方法會指出執行緒是否曾經有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca24d-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="ca24d-117">在觸發未處理的例外狀況回呼或起始原生 JIT 附加時，會保證此方法會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ca24d-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="ca24d-118">不保證[ICorDebugThread 的 GetCurrentException](icordebugthread-getcurrentexception-method.md)方法會傳回未處理的例外狀況;不過，如果在取得未處理的例外狀況回呼或原生 JIT 附加之後，進程尚未繼續，就會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="ca24d-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="ca24d-119">此外，觸發原生 JIT 附加時，有可能（但不太可能）有一個以上的執行緒具有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca24d-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="ca24d-120">在這種情況下，無法判斷哪個例外狀況觸發了 JIT 附加。</span><span class="sxs-lookup"><span data-stu-id="ca24d-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca24d-121">需求</span><span class="sxs-lookup"><span data-stu-id="ca24d-121">Requirements</span></span>  
 <span data-ttu-id="ca24d-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca24d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca24d-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca24d-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca24d-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca24d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca24d-125">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca24d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca24d-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca24d-126">See also</span></span>

- [<span data-ttu-id="ca24d-127">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="ca24d-127">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="ca24d-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ca24d-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ca24d-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="ca24d-129">Debugging</span></span>](index.md)
