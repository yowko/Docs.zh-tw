---
title: ICorDebugController::EnumerateThreads 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17ba15553d2e7dcd2090870eaab54b4c680631f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749341"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="eb857-102">ICorDebugController::EnumerateThreads 方法</span><span class="sxs-lookup"><span data-stu-id="eb857-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="eb857-103">取得作用中的 managed 執行緒處理序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="eb857-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb857-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb857-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb857-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb857-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="eb857-106">[out]「 ICorDebugThreadEnum 」 物件，表示作用中的程序中的所有 managed 執行緒的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="eb857-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb857-107">備註</span><span class="sxs-lookup"><span data-stu-id="eb857-107">Remarks</span></span>  
 <span data-ttu-id="eb857-108">執行緒會被視為作用中後[icordebugmanagedcallback:: Createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)分派回呼之前[icordebugmanagedcallback:: Exitthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)分派回呼.</span><span class="sxs-lookup"><span data-stu-id="eb857-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="eb857-109">Managed 的執行緒不一定能任何受控的框架上其堆疊。</span><span class="sxs-lookup"><span data-stu-id="eb857-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="eb857-110">執行緒可以列舉甚至[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="eb857-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="eb857-111">列舉型別自然會是空的。</span><span class="sxs-lookup"><span data-stu-id="eb857-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb857-112">需求</span><span class="sxs-lookup"><span data-stu-id="eb857-112">Requirements</span></span>  
 <span data-ttu-id="eb857-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb857-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb857-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb857-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb857-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb857-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb857-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb857-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb857-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb857-117">See also</span></span>
