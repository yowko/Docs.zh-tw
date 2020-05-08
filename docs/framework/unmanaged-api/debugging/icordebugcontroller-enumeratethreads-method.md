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
ms.openlocfilehash: 4d69f13d4716b43c815148ff0fe4aa087b57c6e5
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892760"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a><span data-ttu-id="794a9-102">ICorDebugController::EnumerateThreads 方法</span><span class="sxs-lookup"><span data-stu-id="794a9-102">ICorDebugController::EnumerateThreads Method</span></span>
<span data-ttu-id="794a9-103">取得進程中使用中 managed 執行緒的列舉值。</span><span class="sxs-lookup"><span data-stu-id="794a9-103">Gets an enumerator for the active managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="794a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="794a9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="794a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="794a9-105">Parameters</span></span>  
 `ppThreads`  
 <span data-ttu-id="794a9-106">脫銷"ICorDebugThreadEnum" 物件位址的指標，表示進程中所有作用中 managed 執行緒的列舉值。</span><span class="sxs-lookup"><span data-stu-id="794a9-106">[out] A pointer to the address of an "ICorDebugThreadEnum" object that represents an enumerator for all managed threads that are active in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="794a9-107">備註</span><span class="sxs-lookup"><span data-stu-id="794a9-107">Remarks</span></span>  
 <span data-ttu-id="794a9-108">在分派[ICorDebugManagedCallback：： CreateThread](icordebugmanagedcallback-createthread-method.md)回呼之後，以及在分派[ICorDebugManagedCallback：： ExitThread](icordebugmanagedcallback-exitthread-method.md)回呼之前，會將執行緒視為作用中。</span><span class="sxs-lookup"><span data-stu-id="794a9-108">A thread is considered active after the [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) callback has been dispatched and before the [ICorDebugManagedCallback::ExitThread](icordebugmanagedcallback-exitthread-method.md) callback has been dispatched.</span></span> <span data-ttu-id="794a9-109">Managed 執行緒可能不一定會在其堆疊上有任何受控框架。</span><span class="sxs-lookup"><span data-stu-id="794a9-109">A managed thread may not necessarily have any managed frames on its stack.</span></span> <span data-ttu-id="794a9-110">即使在[ICorDebugManagedCallback：： CreateProcess](icordebugmanagedcallback-createprocess-method.md)回呼之前，也可以列舉執行緒。</span><span class="sxs-lookup"><span data-stu-id="794a9-110">Threads can be enumerated even before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="794a9-111">列舉自然會是空的。</span><span class="sxs-lookup"><span data-stu-id="794a9-111">The enumeration will naturally be empty.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="794a9-112">需求</span><span class="sxs-lookup"><span data-stu-id="794a9-112">Requirements</span></span>  
 <span data-ttu-id="794a9-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="794a9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="794a9-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="794a9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="794a9-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="794a9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="794a9-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="794a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794a9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="794a9-117">See also</span></span>
