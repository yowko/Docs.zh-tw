---
title: ICorDebugController::SetAllThreadsDebugState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: c2e8aaa2774e3e2699a73c40804391ca245047b1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976586"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="68b59-102">ICorDebugController::SetAllThreadsDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="68b59-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="68b59-103">設定進程中所有 managed 執行緒的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="68b59-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b59-104">語法</span><span class="sxs-lookup"><span data-stu-id="68b59-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68b59-105">參數</span><span class="sxs-lookup"><span data-stu-id="68b59-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="68b59-106">在"CorDebugThreadState" 列舉的值，指定要進行偵錯工具的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="68b59-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="68b59-107">在"ICorDebugThread" 物件的指標，代表要從 debug 狀態設定中豁免的執行緒。</span><span class="sxs-lookup"><span data-stu-id="68b59-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="68b59-108">如果此值為 null，則不會豁免任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="68b59-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68b59-109">備註</span><span class="sxs-lookup"><span data-stu-id="68b59-109">Remarks</span></span>  
 <span data-ttu-id="68b59-110">方法可能會影響不是透過[EnumerateThreads 方法](icordebugcontroller-enumeratethreads-method.md)顯示的執行緒，因此使用`SetAllThreadsDebugState`方法暫停的執行緒將需要使用`SetAllThreadsDebugState`方法繼續。 `SetAllThreadsDebugState`</span><span class="sxs-lookup"><span data-stu-id="68b59-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68b59-111">需求</span><span class="sxs-lookup"><span data-stu-id="68b59-111">Requirements</span></span>  
 <span data-ttu-id="68b59-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68b59-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68b59-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68b59-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68b59-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68b59-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68b59-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68b59-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b59-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68b59-116">See also</span></span>
