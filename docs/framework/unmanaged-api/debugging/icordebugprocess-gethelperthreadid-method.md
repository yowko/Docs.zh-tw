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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd5e30d08e667dcd5a8be1f9502462f28290068e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987736"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="b38fb-102">ICorDebugProcess::GetHelperThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="b38fb-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="b38fb-103">取得偵錯工具的內部協助程式執行緒的作業系統 (OS) 執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="b38fb-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b38fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="b38fb-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b38fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="b38fb-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="b38fb-106">[out]指標，OS 執行緒偵錯工具的內部協助程式執行緒的 ID。</span><span class="sxs-lookup"><span data-stu-id="b38fb-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b38fb-107">備註</span><span class="sxs-lookup"><span data-stu-id="b38fb-107">Remarks</span></span>  
 <span data-ttu-id="b38fb-108">Managed 和 unmanaged 偵錯期間，是偵錯工具的責任，以確保具有指定識別碼的執行緒保持執行，如果配接器放在偵錯工具的中斷點。</span><span class="sxs-lookup"><span data-stu-id="b38fb-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="b38fb-109">偵錯工具，也可能想要隱藏此執行緒使用者。</span><span class="sxs-lookup"><span data-stu-id="b38fb-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="b38fb-110">如果沒有任何協助程式執行緒，存在於處理程序`GetHelperThreadID`方法會傳回零 \*`pThreadID`。</span><span class="sxs-lookup"><span data-stu-id="b38fb-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="b38fb-111">因為它可能會隨著時間改變，您無法快取的協助程式 」 執行緒的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="b38fb-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="b38fb-112">您必須重新查詢在每個停止事件的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="b38fb-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="b38fb-113">偵錯工具的協助程式執行緒的執行緒識別碼將會是正確的每個非受控[icordebugmanagedcallback:: Createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)事件，因此讓偵錯工具，判斷其協助程式執行緒的執行緒識別碼，並向使用者隱藏它。</span><span class="sxs-lookup"><span data-stu-id="b38fb-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="b38fb-114">被視為期間未受管理的協助程式執行緒的執行緒`ICorDebugManagedCallback::CreateThread`事件永遠不會執行 managed 的使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="b38fb-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b38fb-115">需求</span><span class="sxs-lookup"><span data-stu-id="b38fb-115">Requirements</span></span>  
 <span data-ttu-id="b38fb-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b38fb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b38fb-117">**標頭：** CorDebug.idl。</span><span class="sxs-lookup"><span data-stu-id="b38fb-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="b38fb-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b38fb-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="b38fb-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b38fb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b38fb-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b38fb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
