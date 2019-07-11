---
title: ICorDebugManagedCallback::Exception 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e944a6debf790907b75760c8856ae3a365a84650
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759617"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="a3f45-102">ICorDebugManagedCallback::Exception 方法</span><span class="sxs-lookup"><span data-stu-id="a3f45-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="a3f45-103">例外狀況已擲回從 managed 程式碼會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a3f45-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3f45-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3f45-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3f45-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3f45-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a3f45-106">[in]表示擲回例外狀況所在的應用程式定義域的 ICorDebugAppDomain 物件指標。</span><span class="sxs-lookup"><span data-stu-id="a3f45-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="a3f45-107">[in]ICorDebugThread 物件，表示擲回例外狀況所在的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="a3f45-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="a3f45-108">[in]如果此值為`false`、 例外狀況尚未已由應用程式處理，否則為，例外狀況無法處理，因此將會終止處理序。</span><span class="sxs-lookup"><span data-stu-id="a3f45-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3f45-109">備註</span><span class="sxs-lookup"><span data-stu-id="a3f45-109">Remarks</span></span>  
 <span data-ttu-id="a3f45-110">從執行緒物件，可以擷取特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a3f45-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3f45-111">需求</span><span class="sxs-lookup"><span data-stu-id="a3f45-111">Requirements</span></span>  
 <span data-ttu-id="a3f45-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3f45-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3f45-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3f45-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3f45-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3f45-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3f45-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3f45-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f45-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f45-116">See also</span></span>

- [<span data-ttu-id="a3f45-117">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a3f45-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
