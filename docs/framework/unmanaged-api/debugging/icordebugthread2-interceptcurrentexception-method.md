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
ms.openlocfilehash: d87f07e6cadf8c9b5a4d8bb3063333c26e2c4ff1
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379037"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="a01b2-102">ICorDebugThread2::InterceptCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="a01b2-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="a01b2-103">允許偵錯工具攔截這個執行緒上目前的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a01b2-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="a01b2-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a01b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="a01b2-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="a01b2-106">在表示使用中堆疊框架之 ICorDebugFrame 的指標。</span><span class="sxs-lookup"><span data-stu-id="a01b2-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a01b2-107">備註</span><span class="sxs-lookup"><span data-stu-id="a01b2-107">Remarks</span></span>  
 <span data-ttu-id="a01b2-108">`InterceptCurrentException`可以在例外狀況回呼（[ICorDebugManagedCallback：： Exception](icordebugmanagedcallback-exception-method.md)或[ICorDebugManagedCallback2：： exception](icordebugmanagedcallback2-exception-method.md)）與[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)的相關呼叫之間呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="a01b2-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a01b2-109">需求</span><span class="sxs-lookup"><span data-stu-id="a01b2-109">Requirements</span></span>  
 <span data-ttu-id="a01b2-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a01b2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a01b2-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a01b2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a01b2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a01b2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a01b2-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a01b2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
