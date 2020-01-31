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
ms.openlocfilehash: e7125d923fb1d3757bb4ca53f5a7db806b241dd9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781522"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="fd5b6-102">ICorDebugManagedCallback2::Exception 方法</span><span class="sxs-lookup"><span data-stu-id="fd5b6-102">ICorDebugManagedCallback2::Exception Method</span></span>
<span data-ttu-id="fd5b6-103">通知偵錯工具已開始搜尋例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd5b6-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd5b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd5b6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="fd5b6-106">在ICorDebugAppDomain 物件的指標，表示包含擲回例外狀況之執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="fd5b6-107">在ICorDebugThread 物件的指標，表示擲回例外狀況的執行緒。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="fd5b6-108">在代表框架的 ICorDebugFrame 物件指標，由 `dwEventType` 參數決定。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="fd5b6-109">如需詳細資訊，請參閱備註一節中的表格。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="fd5b6-110">在指定位移的整數，由 `dwEventType` 參數決定。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="fd5b6-111">如需詳細資訊，請參閱備註一節中的表格。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="fd5b6-112">在CorDebugExceptionCallbackType 列舉的值，指定這個例外狀況回呼的類型。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fd5b6-113">在[CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md)列舉的值，指定例外狀況的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-113">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd5b6-114">備註</span><span class="sxs-lookup"><span data-stu-id="fd5b6-114">Remarks</span></span>  
 <span data-ttu-id="fd5b6-115">在例外狀況處理常式的搜尋階段，會在不同的時間點呼叫 `Exception` 回呼。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="fd5b6-116">也就是說，它可以在回溯例外狀況時呼叫多次。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="fd5b6-117">所處理的例外狀況可以從 `pThread` 參數所參考的 ICorDebugThread 物件中抓取。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="fd5b6-118">特定的框架和位移取決於 `dwEventType` 參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="fd5b6-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="fd5b6-119">`dwEventType` 的值</span><span class="sxs-lookup"><span data-stu-id="fd5b6-119">Value of `dwEventType`</span></span>|<span data-ttu-id="fd5b6-120">`pFrame` 的值</span><span class="sxs-lookup"><span data-stu-id="fd5b6-120">Value of `pFrame`</span></span>|<span data-ttu-id="fd5b6-121">`nOffset` 的值</span><span class="sxs-lookup"><span data-stu-id="fd5b6-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="fd5b6-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="fd5b6-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="fd5b6-123">擲回例外狀況的框架。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-123">The frame that threw the exception.</span></span>|<span data-ttu-id="fd5b6-124">框架中的指令指標。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="fd5b6-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="fd5b6-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="fd5b6-126">最接近所擲回例外狀況點的使用者程式碼框架。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="fd5b6-127">框架中的指令指標。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="fd5b6-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="fd5b6-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="fd5b6-129">包含 catch 處理常式的框架。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="fd5b6-130">Catch 處理常式開頭的 Microsoft 中繼語言（MSIL）位移。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="fd5b6-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="fd5b6-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="fd5b6-132">NULL</span><span class="sxs-lookup"><span data-stu-id="fd5b6-132">NULL</span></span>|<span data-ttu-id="fd5b6-133">Useraccountcontrol.</span><span class="sxs-lookup"><span data-stu-id="fd5b6-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd5b6-134">需求</span><span class="sxs-lookup"><span data-stu-id="fd5b6-134">Requirements</span></span>  
 <span data-ttu-id="fd5b6-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd5b6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd5b6-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd5b6-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd5b6-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd5b6-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd5b6-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd5b6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5b6-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd5b6-139">See also</span></span>

- [<span data-ttu-id="fd5b6-140">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="fd5b6-140">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="fd5b6-141">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fd5b6-141">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
