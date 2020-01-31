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
ms.openlocfilehash: d0dc301c67d09ebb15bf47cef15e642fb7c78fb9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792611"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="8b3b9-102">ICorDebugProcess::GetHelperThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="8b3b9-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="8b3b9-103">取得偵錯工具內部 helper 執行緒的作業系統（OS）執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b3b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b3b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b3b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b3b9-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="8b3b9-106">脫銷偵錯工具內部 helper 執行緒的 OS 執行緒識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b3b9-107">備註</span><span class="sxs-lookup"><span data-stu-id="8b3b9-107">Remarks</span></span>  
 <span data-ttu-id="8b3b9-108">在受控和非受控的調試過程中，偵錯工具必須負責確保具有指定識別碼的執行緒在到達偵錯工具所放置的中斷點時，仍會繼續運作。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="8b3b9-109">偵錯工具可能也會想要從使用者隱藏此執行緒。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="8b3b9-110">如果進程中沒有 helper 執行緒，`GetHelperThreadID` 方法會在 \*`pThreadID`中傳回零。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="8b3b9-111">您無法快取 helper 執行緒的執行緒識別碼，因為它可能會隨著時間而改變。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="8b3b9-112">您必須在每個停止事件時重新查詢執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="8b3b9-113">偵錯工具 helper 執行緒的執行緒識別碼在每個非受控[ICorDebugManagedCallback：： CreateThread](icordebugmanagedcallback-createthread-method.md)事件中都是正確的，因此可讓偵錯工具判斷其 helper 執行緒的執行緒識別碼，並將其從使用者中隱藏。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="8b3b9-114">在非受控 `ICorDebugManagedCallback::CreateThread` 事件期間識別為 helper 執行緒的執行緒，將永遠不會執行 managed 使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b3b9-115">需求</span><span class="sxs-lookup"><span data-stu-id="8b3b9-115">Requirements</span></span>  
 <span data-ttu-id="8b3b9-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b3b9-117">**標頭：** Cordebug.h .idl。</span><span class="sxs-lookup"><span data-stu-id="8b3b9-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="8b3b9-118">Cordebug.h。h</span><span class="sxs-lookup"><span data-stu-id="8b3b9-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="8b3b9-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b3b9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b3b9-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b3b9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
