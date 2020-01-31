---
title: ICorDebugThread2::InterceptCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: c25a03ef5bbba18da31787c911f83a1348badd4b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791457"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="81013-102">ICorDebugThread2::InterceptCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="81013-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="81013-103">允許偵錯工具攔截這個執行緒上目前的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="81013-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81013-104">語法</span><span class="sxs-lookup"><span data-stu-id="81013-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81013-105">參數</span><span class="sxs-lookup"><span data-stu-id="81013-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="81013-106">在表示使用中堆疊框架之 ICorDebugFrame 的指標。</span><span class="sxs-lookup"><span data-stu-id="81013-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81013-107">備註</span><span class="sxs-lookup"><span data-stu-id="81013-107">Remarks</span></span>  
 <span data-ttu-id="81013-108">可以在例外狀況回呼（[ICorDebugManagedCallback：： exception](icordebugmanagedcallback-exception-method.md)或[ICorDebugManagedCallback2：： Exception](icordebugmanagedcallback2-exception-method.md)）與[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)的相關呼叫之間呼叫 `InterceptCurrentException` 方法。</span><span class="sxs-lookup"><span data-stu-id="81013-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81013-109">需求</span><span class="sxs-lookup"><span data-stu-id="81013-109">Requirements</span></span>  
 <span data-ttu-id="81013-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81013-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81013-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81013-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81013-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81013-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81013-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81013-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
