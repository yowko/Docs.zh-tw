---
title: "ICorDebugThread4::HadUnhandledException 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.HadUnhandledException Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ea29fa02e74c204cde003b18520bf512b0d21d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4hadunhandledexception-method"></a><span data-ttu-id="d2cd0-102">ICorDebugThread4::HadUnhandledException 方法</span><span class="sxs-lookup"><span data-stu-id="d2cd0-102">ICorDebugThread4::HadUnhandledException Method</span></span>
<span data-ttu-id="d2cd0-103">指出執行緒是否有曾經處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-103">Indicates whether the thread has ever had an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2cd0-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2cd0-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2cd0-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2cd0-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="d2cd0-106">[out]之已排序列舉的位址指標[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-106">[out] A pointer to the address of an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2cd0-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d2cd0-107">Return Value</span></span>  
 <span data-ttu-id="d2cd0-108">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d2cd0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d2cd0-109">HRESULT</span></span>|<span data-ttu-id="d2cd0-110">描述</span><span class="sxs-lookup"><span data-stu-id="d2cd0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d2cd0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d2cd0-111">S_OK</span></span>|<span data-ttu-id="d2cd0-112">執行緒已自其建立後的未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-112">The thread has had an unhandled exception since its creation.</span></span>|  
|<span data-ttu-id="d2cd0-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d2cd0-113">S_FALSE</span></span>|<span data-ttu-id="d2cd0-114">執行緒從未安裝過處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-114">The thread has never had an unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2cd0-115">備註</span><span class="sxs-lookup"><span data-stu-id="d2cd0-115">Remarks</span></span>  
 <span data-ttu-id="d2cd0-116">這個方法會指出執行緒是否有曾經處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-116">This method indicates whether the thread has ever had an unhandled exception.</span></span> <span data-ttu-id="d2cd0-117">根據時間就會觸發未處理例外狀況回呼或起始原生 JIT 附加時，這個方法保證會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-117">By the time the unhandled exception callback is triggered or native JIT-attach is initiated, this method is guaranteed to return S_OK.</span></span> <span data-ttu-id="d2cd0-118">不保證， [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)方法會傳回未處理的例外狀況; 不過，它將如果處理程序已不尚未繼續取得未處理例外狀況回呼之後，或在原生 JIT 附加。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-118">There is no guarantee that the [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md) method will return the unhandled exception; however, it will if the process has not yet been continued after getting the unhandled exception callback or upon native JIT-attach.</span></span> <span data-ttu-id="d2cd0-119">此外，它有可能 （雖然可能性不大） 有多個執行緒的未處理例外狀況在原生 JIT 附加，就會觸發的階段。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-119">Furthermore, it is possible (although unlikely) to have more than one thread with an unhandled exception at the time native JIT-attach is triggered.</span></span> <span data-ttu-id="d2cd0-120">在此情況下沒有任何方式可判斷哪些例外狀況觸發 JIT 附加。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-120">In such a case there is no way to determine which exception triggered the JIT-attach.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2cd0-121">需求</span><span class="sxs-lookup"><span data-stu-id="d2cd0-121">Requirements</span></span>  
 <span data-ttu-id="d2cd0-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2cd0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2cd0-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2cd0-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2cd0-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2cd0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2cd0-125">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2cd0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2cd0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2cd0-126">See Also</span></span>  
 [<span data-ttu-id="d2cd0-127">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="d2cd0-127">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="d2cd0-128">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d2cd0-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d2cd0-129">偵錯</span><span class="sxs-lookup"><span data-stu-id="d2cd0-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
