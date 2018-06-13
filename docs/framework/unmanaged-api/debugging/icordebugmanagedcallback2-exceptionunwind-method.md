---
title: ICorDebugManagedCallback2::ExceptionUnwind 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92c4f488dcdc5712dcd2632f489fb0cd65d05ee6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416253"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="c5b4f-102">ICorDebugManagedCallback2::ExceptionUnwind 方法</span><span class="sxs-lookup"><span data-stu-id="c5b4f-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="c5b4f-103">提供例外狀況回溯程序期間的狀態通知。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5b4f-104">Syntax</span></span>  
  
```  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5b4f-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5b4f-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c5b4f-106">[in]表示包含擲回例外狀況所在的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="c5b4f-107">[in]表示擲回例外狀況所在的執行緒 ICorDebugThread 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="c5b4f-108">[in]CorDebugExceptionUnwindCallbackType 列舉型別會指定回呼在回溯階段期間通知的事件值。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c5b4f-109">[in]值為[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)列舉，指定例外狀況的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-109">[in] A value of the [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5b4f-110">備註</span><span class="sxs-lookup"><span data-stu-id="c5b4f-110">Remarks</span></span>  
 <span data-ttu-id="c5b4f-111">`ExceptionUnwind` 會在回溯階段的例外狀況處理程序期間呼叫的各個點上。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="c5b4f-112">`ExceptionUnwind` 可以被呼叫一次以上時回溯單一例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="c5b4f-113">如果`dwEventType`= DEBUG_EXCEPTION_INTERCEPTED，指令指標會在執行緒，在之前的序列點的分葉框架 （這可能是之前的幾個指令） 造成例外狀況的指示。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5b4f-114">需求</span><span class="sxs-lookup"><span data-stu-id="c5b4f-114">Requirements</span></span>  
 <span data-ttu-id="c5b4f-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5b4f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5b4f-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5b4f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5b4f-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5b4f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5b4f-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5b4f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5b4f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5b4f-119">See Also</span></span>  
 [<span data-ttu-id="c5b4f-120">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="c5b4f-120">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="c5b4f-121">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c5b4f-121">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
