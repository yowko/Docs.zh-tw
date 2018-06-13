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
ms.openlocfilehash: 6f8276e2a8fd1bdc546add2ae1ca5d96298186c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412827"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="cab5e-102">ICorDebugController::EnumerateThreads 方法</span><span class="sxs-lookup"><span data-stu-id="cab5e-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="cab5e-103">取得作用中的 managed 執行緒處理序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="cab5e-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cab5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="cab5e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cab5e-105">參數</span><span class="sxs-lookup"><span data-stu-id="cab5e-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="cab5e-106">[out]表示處理序中作用中的所有 managed 執行緒的列舉值 」 ICorDebugThreadEnum 」 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="cab5e-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cab5e-107">備註</span><span class="sxs-lookup"><span data-stu-id="cab5e-107">Remarks</span></span>  
 <span data-ttu-id="cab5e-108">執行緒會被視為 active 之後[icordebugmanagedcallback:: Createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)分派回呼之前[icordebugmanagedcallback:: Exitthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)分派回撥.</span><span class="sxs-lookup"><span data-stu-id="cab5e-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="cab5e-109">Managed 的執行緒不一定能有任何 managed 的框架其堆疊上。</span><span class="sxs-lookup"><span data-stu-id="cab5e-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="cab5e-110">執行緒可以甚至列舉[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="cab5e-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="cab5e-111">列舉型別自然會為空白。</span><span class="sxs-lookup"><span data-stu-id="cab5e-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cab5e-112">需求</span><span class="sxs-lookup"><span data-stu-id="cab5e-112">Requirements</span></span>  
 <span data-ttu-id="cab5e-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cab5e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cab5e-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cab5e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cab5e-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cab5e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cab5e-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cab5e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cab5e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cab5e-117">See Also</span></span>  
 
