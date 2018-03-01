---
title: "ICorDebugManagedCallback2::Exception 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79a8fa4709aeb04164bd1c2da07607435b76fff5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="2d49d-102">ICorDebugManagedCallback2::Exception 方法</span><span class="sxs-lookup"><span data-stu-id="2d49d-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="2d49d-103">告知偵錯工具搜尋例外狀況處理常式已開始。</span><span class="sxs-lookup"><span data-stu-id="2d49d-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d49d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d49d-104">Syntax</span></span>  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d49d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d49d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="2d49d-106">[in]表示包含擲回例外狀況所在的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="2d49d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="2d49d-107">[in]表示擲回例外狀況所在的執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="2d49d-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="2d49d-108">[in]ICorDebugFrame 物件，表示在範圍內，由指標`dwEventType`參數。</span><span class="sxs-lookup"><span data-stu-id="2d49d-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="2d49d-109">如需詳細資訊，請參閱 < 備註 > 一節中的資料表。</span><span class="sxs-lookup"><span data-stu-id="2d49d-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="2d49d-110">[in]整數，取決於指定位移，`dwEventType`參數。</span><span class="sxs-lookup"><span data-stu-id="2d49d-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="2d49d-111">如需詳細資訊，請參閱 < 備註 > 一節中的資料表。</span><span class="sxs-lookup"><span data-stu-id="2d49d-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="2d49d-112">[in]指定此例外狀況回呼類型 CorDebugExceptionCallbackType 列舉值。</span><span class="sxs-lookup"><span data-stu-id="2d49d-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2d49d-113">[in]值為[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)列舉，指定例外狀況的其他資訊</span><span class="sxs-lookup"><span data-stu-id="2d49d-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d49d-114">備註</span><span class="sxs-lookup"><span data-stu-id="2d49d-114">Remarks</span></span>  
 <span data-ttu-id="2d49d-115">`Exception`回呼例外狀況處理程序的搜尋階段期間，會呼叫在不同時間點。</span><span class="sxs-lookup"><span data-stu-id="2d49d-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="2d49d-116">也就是說，它可以呼叫超過一次而回溯例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2d49d-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="2d49d-117">正在處理的例外狀況可以從所參考的 ICorDebugThread 物件擷取`pThread`參數。</span><span class="sxs-lookup"><span data-stu-id="2d49d-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="2d49d-118">特定的畫面格和位移，由`dwEventType`參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2d49d-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="2d49d-119">`dwEventType` 的值</span><span class="sxs-lookup"><span data-stu-id="2d49d-119">Value of `dwEventType`</span></span>|<span data-ttu-id="2d49d-120">`pFrame` 的值</span><span class="sxs-lookup"><span data-stu-id="2d49d-120">Value of `pFrame`</span></span>|<span data-ttu-id="2d49d-121">`nOffset` 的值</span><span class="sxs-lookup"><span data-stu-id="2d49d-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="2d49d-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2d49d-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="2d49d-123">擲回例外狀況框架。</span><span class="sxs-lookup"><span data-stu-id="2d49d-123">The frame that threw the exception.</span></span>|<span data-ttu-id="2d49d-124">指令指標框架中。</span><span class="sxs-lookup"><span data-stu-id="2d49d-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="2d49d-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2d49d-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="2d49d-126">最接近擲回的例外狀況位置之使用者程式碼框架。</span><span class="sxs-lookup"><span data-stu-id="2d49d-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="2d49d-127">指令指標框架中。</span><span class="sxs-lookup"><span data-stu-id="2d49d-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="2d49d-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="2d49d-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="2d49d-129">包含 catch 處理常式的框架。</span><span class="sxs-lookup"><span data-stu-id="2d49d-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="2d49d-130">Catch 處理常式開頭的 Microsoft intermediate language (MSIL) 位移。</span><span class="sxs-lookup"><span data-stu-id="2d49d-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="2d49d-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="2d49d-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="2d49d-132">NULL</span><span class="sxs-lookup"><span data-stu-id="2d49d-132">NULL</span></span>|<span data-ttu-id="2d49d-133">未定義。</span><span class="sxs-lookup"><span data-stu-id="2d49d-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d49d-134">需求</span><span class="sxs-lookup"><span data-stu-id="2d49d-134">Requirements</span></span>  
 <span data-ttu-id="2d49d-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d49d-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d49d-136">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d49d-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d49d-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d49d-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d49d-138">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d49d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d49d-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d49d-139">See Also</span></span>  
 [<span data-ttu-id="2d49d-140">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="2d49d-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="2d49d-141">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2d49d-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
