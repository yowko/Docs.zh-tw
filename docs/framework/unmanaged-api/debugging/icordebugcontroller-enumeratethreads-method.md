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
ms.openlocfilehash: 73b84179717e4b96a5c3637b85ae936a23bbf42d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748862"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="06f25-102">ICorDebugController::EnumerateThreads 方法</span><span class="sxs-lookup"><span data-stu-id="06f25-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="06f25-103">取得作用中的 managed 執行緒處理序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="06f25-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f25-104">語法</span><span class="sxs-lookup"><span data-stu-id="06f25-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06f25-105">參數</span><span class="sxs-lookup"><span data-stu-id="06f25-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="06f25-106">[out]「 ICorDebugThreadEnum 」 物件，表示作用中的程序中的所有 managed 執行緒的列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="06f25-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06f25-107">備註</span><span class="sxs-lookup"><span data-stu-id="06f25-107">Remarks</span></span>  
 <span data-ttu-id="06f25-108">執行緒會被視為作用中後[icordebugmanagedcallback:: Createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)分派回呼之前[icordebugmanagedcallback:: Exitthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)分派回呼.</span><span class="sxs-lookup"><span data-stu-id="06f25-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="06f25-109">Managed 的執行緒不一定能任何受控的框架上其堆疊。</span><span class="sxs-lookup"><span data-stu-id="06f25-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="06f25-110">執行緒可以列舉甚至[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="06f25-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="06f25-111">列舉型別自然會是空的。</span><span class="sxs-lookup"><span data-stu-id="06f25-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06f25-112">需求</span><span class="sxs-lookup"><span data-stu-id="06f25-112">Requirements</span></span>  
 <span data-ttu-id="06f25-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06f25-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06f25-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06f25-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06f25-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06f25-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06f25-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06f25-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f25-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06f25-117">See also</span></span>
