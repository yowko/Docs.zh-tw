---
title: ICorDebugController::Continue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62e2be44165472e2fbf368f61b865d39a5e9fc28
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395458"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="e6305-102">ICorDebugController::Continue 方法</span><span class="sxs-lookup"><span data-stu-id="e6305-102">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="e6305-103">呼叫[Stop 方法](icordebugcontroller-stop-method.md)之後，繼續執行 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="e6305-103">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="e6305-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6305-104">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="e6305-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6305-105">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="e6305-106">在如果從頻外事件繼續，請將設定為 `true`;否則，設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e6305-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6305-107">備註</span><span class="sxs-lookup"><span data-stu-id="e6305-107">Remarks</span></span>

<span data-ttu-id="e6305-108">`Continue` 會在呼叫 `ICorDebugController::Stop` 方法之後繼續處理。</span><span class="sxs-lookup"><span data-stu-id="e6305-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="e6305-109">執行混合模式的偵錯工具時，除非您從頻外事件繼續，否則請勿在 Win32 事件執行緒上呼叫 `Continue`。</span><span class="sxs-lookup"><span data-stu-id="e6305-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="e6305-110">*內建事件*是 managed 事件或一般非受控事件，在此期間，偵錯工具支援與進程的受管理狀態互動。</span><span class="sxs-lookup"><span data-stu-id="e6305-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="e6305-111">在此情況下，偵錯工具會接收[ICorDebugUnmanagedCallback：:D ebugevent](icordebugunmanagedcallback-debugevent-method.md)回呼，並將其 `fOutOfBand` 參數設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="e6305-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="e6305-112">*頻外事件*是一個不受管理的事件，在此情況下，當進程因事件而停止時，無法與處理常式的受管理狀態互動。</span><span class="sxs-lookup"><span data-stu-id="e6305-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="e6305-113">在此情況下，偵錯工具會接收 @no__t 0 回呼，並將其 `fOutOfBand` 參數設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e6305-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6305-114">需求</span><span class="sxs-lookup"><span data-stu-id="e6305-114">Requirements</span></span>

<span data-ttu-id="e6305-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6305-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="e6305-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6305-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="e6305-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6305-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e6305-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6305-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
