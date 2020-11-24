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
ms.openlocfilehash: c5be9231bcd5aaddfa0cf1b0051f8e1184faef04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687628"
---
# <a name="icordebugmanagedcallback2exception-method"></a><span data-ttu-id="06169-102">ICorDebugManagedCallback2::Exception 方法</span><span class="sxs-lookup"><span data-stu-id="06169-102">ICorDebugManagedCallback2::Exception Method</span></span>

<span data-ttu-id="06169-103">通知偵錯工具已開始搜尋例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="06169-103">Notifies the debugger that a search for an exception handler has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06169-104">語法</span><span class="sxs-lookup"><span data-stu-id="06169-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="06169-105">參數</span><span class="sxs-lookup"><span data-stu-id="06169-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="06169-106">在ICorDebugAppDomain 物件的指標，代表包含擲回例外狀況之執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="06169-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="06169-107">在代表擲回例外狀況之執行緒的 ICorDebugThread 物件指標。</span><span class="sxs-lookup"><span data-stu-id="06169-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="06169-108">在ICorDebugFrame 物件的指標，該物件表示框架（由參數所決定） `dwEventType` 。</span><span class="sxs-lookup"><span data-stu-id="06169-108">[in] A pointer to an ICorDebugFrame object that represents a frame, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="06169-109">如需詳細資訊，請參閱「備註」一節中的表格。</span><span class="sxs-lookup"><span data-stu-id="06169-109">For more information, see the table in the Remarks section.</span></span>  
  
 `nOffset`  
 <span data-ttu-id="06169-110">在指定位移的整數，由參數所決定 `dwEventType` 。</span><span class="sxs-lookup"><span data-stu-id="06169-110">[in] An integer that specifies an offset, as determined by the `dwEventType` parameter.</span></span> <span data-ttu-id="06169-111">如需詳細資訊，請參閱「備註」一節中的表格。</span><span class="sxs-lookup"><span data-stu-id="06169-111">For more information, see the table in the Remarks section.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="06169-112">在CorDebugExceptionCallbackType 列舉的值，這個值會指定這個例外狀況回呼的型別。</span><span class="sxs-lookup"><span data-stu-id="06169-112">[in] A value of the CorDebugExceptionCallbackType enumeration that specifies the type of this exception callback.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="06169-113">在 [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) 列舉的值，指定例外狀況的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="06169-113">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06169-114">備註</span><span class="sxs-lookup"><span data-stu-id="06169-114">Remarks</span></span>  

 <span data-ttu-id="06169-115">在 `Exception` 例外狀況處理常式的搜尋階段，會在不同的點呼叫回呼。</span><span class="sxs-lookup"><span data-stu-id="06169-115">The `Exception` callback is called at various points during the search phase of the exception-handling process.</span></span> <span data-ttu-id="06169-116">也就是說，它可以在回溯例外狀況時呼叫一次以上。</span><span class="sxs-lookup"><span data-stu-id="06169-116">That is, it can be called more than once while unwinding an exception.</span></span>  
  
 <span data-ttu-id="06169-117">所處理的例外狀況可以從參數所參考的 ICorDebugThread 物件中取出 `pThread` 。</span><span class="sxs-lookup"><span data-stu-id="06169-117">The exception being processed can be retrieved from the ICorDebugThread object referenced by the `pThread` parameter.</span></span>  
  
 <span data-ttu-id="06169-118">特定的畫面格和位移取決於參數，如下所示 `dwEventType` ：</span><span class="sxs-lookup"><span data-stu-id="06169-118">The particular frame and offset are determined by the `dwEventType` parameter as follows:</span></span>  
  
|<span data-ttu-id="06169-119">`dwEventType` 的值</span><span class="sxs-lookup"><span data-stu-id="06169-119">Value of `dwEventType`</span></span>|<span data-ttu-id="06169-120">`pFrame` 的值</span><span class="sxs-lookup"><span data-stu-id="06169-120">Value of `pFrame`</span></span>|<span data-ttu-id="06169-121">`nOffset` 的值</span><span class="sxs-lookup"><span data-stu-id="06169-121">Value of `nOffset`</span></span>|  
|----------------------------|-----------------------|------------------------|  
|<span data-ttu-id="06169-122">DEBUG_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="06169-122">DEBUG_EXCEPTION_FIRST_CHANCE</span></span>|<span data-ttu-id="06169-123">擲回例外狀況的框架。</span><span class="sxs-lookup"><span data-stu-id="06169-123">The frame that threw the exception.</span></span>|<span data-ttu-id="06169-124">框架中的指令指標。</span><span class="sxs-lookup"><span data-stu-id="06169-124">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="06169-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="06169-125">DEBUG_EXCEPTION_USER_FIRST_CHANCE</span></span>|<span data-ttu-id="06169-126">最接近擲回之例外狀況點的使用者程式碼框架。</span><span class="sxs-lookup"><span data-stu-id="06169-126">The user-code frame closest to the point of the thrown exception.</span></span>|<span data-ttu-id="06169-127">框架中的指令指標。</span><span class="sxs-lookup"><span data-stu-id="06169-127">The instruction pointer in the frame.</span></span>|  
|<span data-ttu-id="06169-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="06169-128">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND</span></span>|<span data-ttu-id="06169-129">包含 catch 處理常式的框架。</span><span class="sxs-lookup"><span data-stu-id="06169-129">The frame that contains the catch handler.</span></span>|<span data-ttu-id="06169-130">Microsoft 中繼語言 (MSIL，) catch 處理常式開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="06169-130">The Microsoft intermediate language (MSIL) offset of the beginning of the catch handler.</span></span>|  
|<span data-ttu-id="06169-131">DEBUG_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="06169-131">DEBUG_EXCEPTION_UNHANDLED</span></span>|<span data-ttu-id="06169-132">NULL</span><span class="sxs-lookup"><span data-stu-id="06169-132">NULL</span></span>|<span data-ttu-id="06169-133">未定義。</span><span class="sxs-lookup"><span data-stu-id="06169-133">Undefined.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06169-134">需求</span><span class="sxs-lookup"><span data-stu-id="06169-134">Requirements</span></span>  

 <span data-ttu-id="06169-135">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06169-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06169-136">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06169-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06169-137">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06169-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06169-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06169-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06169-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06169-139">See also</span></span>

- [<span data-ttu-id="06169-140">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="06169-140">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="06169-141">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="06169-141">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
