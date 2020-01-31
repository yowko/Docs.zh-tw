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
ms.openlocfilehash: 482afd09ce370fb1247864b9ac2032ee7e3a1dca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788282"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="89811-102">ICorDebugManagedCallback2::ExceptionUnwind 方法</span><span class="sxs-lookup"><span data-stu-id="89811-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>
<span data-ttu-id="89811-103">提供例外狀況回溯程式期間的狀態通知。</span><span class="sxs-lookup"><span data-stu-id="89811-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89811-104">語法</span><span class="sxs-lookup"><span data-stu-id="89811-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89811-105">參數</span><span class="sxs-lookup"><span data-stu-id="89811-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="89811-106">在ICorDebugAppDomain 物件的指標，表示包含擲回例外狀況之執行緒的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="89811-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="89811-107">在ICorDebugThread 物件的指標，表示擲回例外狀況的執行緒。</span><span class="sxs-lookup"><span data-stu-id="89811-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="89811-108">在CorDebugExceptionUnwindCallbackType 列舉的值，指定在回溯階段期間由回呼所通知的事件。</span><span class="sxs-lookup"><span data-stu-id="89811-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="89811-109">在[CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md)列舉的值，指定例外狀況的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="89811-109">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89811-110">備註</span><span class="sxs-lookup"><span data-stu-id="89811-110">Remarks</span></span>  
 <span data-ttu-id="89811-111">在例外狀況處理常式的回溯階段期間，會在不同的時間點呼叫 `ExceptionUnwind`。</span><span class="sxs-lookup"><span data-stu-id="89811-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="89811-112">在回溯單一例外狀況時，可以多次呼叫 `ExceptionUnwind`。</span><span class="sxs-lookup"><span data-stu-id="89811-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="89811-113">如果 `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED，指令指標將會線上程的分葉框架中，在此位置之前的序列點（這可能是之前的幾個指示）導致例外狀況的指令。</span><span class="sxs-lookup"><span data-stu-id="89811-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89811-114">需求</span><span class="sxs-lookup"><span data-stu-id="89811-114">Requirements</span></span>  
 <span data-ttu-id="89811-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89811-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89811-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89811-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89811-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89811-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89811-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89811-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89811-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="89811-119">See also</span></span>

- [<span data-ttu-id="89811-120">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="89811-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="89811-121">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="89811-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
