---
title: ICorDebugManagedCallback2::Exception 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f776f20f163df91d65509e5dbab31fe9c29a965
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492097"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="33e91-102">ICorDebugManagedCallback2::Exception 方法</span><span class="sxs-lookup"><span data-stu-id="33e91-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="33e91-103">已開始搜尋例外狀況處理常式會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="33e91-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e91-104">語法</span><span class="sxs-lookup"><span data-stu-id="33e91-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="33e91-105">參數</span><span class="sxs-lookup"><span data-stu-id="33e91-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="33e91-106">[in]ICorDebugAppDomain 物件，表示應用程式定義域包含的執行緒例外狀況的指標。</span><span class="sxs-lookup"><span data-stu-id="33e91-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="33e91-107">[in]ICorDebugThread 物件，表示的執行緒例外狀況的指標。</span><span class="sxs-lookup"><span data-stu-id="33e91-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="33e91-108">[in]ICorDebugFrame 物件，表示在範圍內，由指標`dwEventType`參數。</span><span class="sxs-lookup"><span data-stu-id="33e91-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="33e91-109">如需詳細資訊，請參閱 < 備註 > 一節的表格。</span><span class="sxs-lookup"><span data-stu-id="33e91-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="33e91-110">[in]整數，指定位移，由`dwEventType`參數。</span><span class="sxs-lookup"><span data-stu-id="33e91-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="33e91-111">如需詳細資訊，請參閱 < 備註 > 一節的表格。</span><span class="sxs-lookup"><span data-stu-id="33e91-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="33e91-112">[in]CorDebugExceptionCallbackType 列舉，指定此例外狀況的回呼類型的值。</span><span class="sxs-lookup"><span data-stu-id="33e91-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="33e91-113">[in]值為[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)列舉，指定例外狀況的其他資訊</span><span class="sxs-lookup"><span data-stu-id="33e91-113">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33e91-114">備註</span><span class="sxs-lookup"><span data-stu-id="33e91-114">Remarks</span></span>  
 <span data-ttu-id="33e91-115">`Exception`回呼例外狀況處理程序的 「 搜尋 」 階段期間，會呼叫在不同的點。</span><span class="sxs-lookup"><span data-stu-id="33e91-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="33e91-116">也就是說，它可以呼叫超過一次而回溯例外狀況。</span><span class="sxs-lookup"><span data-stu-id="33e91-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="33e91-117">正在處理的例外狀況可以擷取從所參考的 ICorDebugThread 物件`pThread`參數。</span><span class="sxs-lookup"><span data-stu-id="33e91-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="33e91-118">特定畫面格和位移取決於`dwEventType`參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="33e91-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="33e91-119">`dwEventType` 的值</span><span class="sxs-lookup"><span data-stu-id="33e91-119">Value of `dwEventType`</span></span>|<span data-ttu-id="33e91-120">`pFrame` 的值</span><span class="sxs-lookup"><span data-stu-id="33e91-120">Value of `pFrame`</span></span>|<span data-ttu-id="33e91-121">`nOffset` 的值</span><span class="sxs-lookup"><span data-stu-id="33e91-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="33e91-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="33e91-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="33e91-123">擲回例外狀況框架。</span><span class="sxs-lookup"><span data-stu-id="33e91-123">The frame that threw the exception.</span></span>|<span data-ttu-id="33e91-124">指令指標框架中。</span><span class="sxs-lookup"><span data-stu-id="33e91-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="33e91-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="33e91-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="33e91-126">擲回的例外狀況的點最接近的使用者程式碼框架。</span><span class="sxs-lookup"><span data-stu-id="33e91-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="33e91-127">指令指標框架中。</span><span class="sxs-lookup"><span data-stu-id="33e91-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="33e91-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="33e91-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="33e91-129">包含 catch 處理常式之框架。</span><span class="sxs-lookup"><span data-stu-id="33e91-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="33e91-130">Microsoft intermediate language (MSIL) 位移開頭的 catch 處理常式。</span><span class="sxs-lookup"><span data-stu-id="33e91-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="33e91-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="33e91-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="33e91-132">NULL</span><span class="sxs-lookup"><span data-stu-id="33e91-132">NULL</span></span>|<span data-ttu-id="33e91-133">未定義。</span><span class="sxs-lookup"><span data-stu-id="33e91-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33e91-134">需求</span><span class="sxs-lookup"><span data-stu-id="33e91-134">Requirements</span></span>  
 <span data-ttu-id="33e91-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33e91-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33e91-136">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33e91-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33e91-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33e91-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33e91-138">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33e91-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e91-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33e91-139">See also</span></span>
- [<span data-ttu-id="33e91-140">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="33e91-140">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="33e91-141">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="33e91-141">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
