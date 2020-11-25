---
title: ICorDebugProcess::GetHelperThreadID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: 77cc658e28c7a69d8c4aeeed2f3e7ea40f0d2af6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724568"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="0a0e4-102">ICorDebugProcess::GetHelperThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="0a0e4-102">ICorDebugProcess::GetHelperThreadID Method</span></span>

<span data-ttu-id="0a0e4-103">取得作業系統 (作業系統) 偵錯工具內部 helper 執行緒的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a0e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a0e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a0e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="0a0e4-105">Parameters</span></span>  

 `pThreadID`  
 <span data-ttu-id="0a0e4-106">擴展偵錯工具之內部 helper 執行緒的 OS 執行緒識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a0e4-107">備註</span><span class="sxs-lookup"><span data-stu-id="0a0e4-107">Remarks</span></span>  

 <span data-ttu-id="0a0e4-108">在受控和非受控的偵錯工具期間，偵錯工具必須負責確保具有指定識別碼的執行緒在叫用偵錯工具所放置的中斷點時仍繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="0a0e4-109">偵錯工具也可能會想要從使用者隱藏這個執行緒。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="0a0e4-110">如果進程中沒有 helper 執行緒存在， `GetHelperThreadID` 方法會在 \* 中傳回零 `pThreadID` 。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="0a0e4-111">您無法快取 helper 執行緒的執行緒識別碼，因為它可能會隨著時間而變更。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="0a0e4-112">您必須在每次停止事件時重新查詢執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="0a0e4-113">偵錯工具 helper 執行緒的執行緒識別碼在每個非受控 [ICorDebugManagedCallback：： CreateThread](icordebugmanagedcallback-createthread-method.md) 事件上都是正確的，因此可讓偵錯工具判斷其 helper 執行緒的執行緒識別碼，並將其從使用者中隱藏。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="0a0e4-114">在非受控事件期間識別為 helper 執行緒的執行緒 `ICorDebugManagedCallback::CreateThread` 永遠不會執行受管理的使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a0e4-115">需求</span><span class="sxs-lookup"><span data-stu-id="0a0e4-115">Requirements</span></span>  

 <span data-ttu-id="0a0e4-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a0e4-117">**標頭：** Cordebug.h .idl。</span><span class="sxs-lookup"><span data-stu-id="0a0e4-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="0a0e4-118">Cordebug.h。h</span><span class="sxs-lookup"><span data-stu-id="0a0e4-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="0a0e4-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a0e4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a0e4-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a0e4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
