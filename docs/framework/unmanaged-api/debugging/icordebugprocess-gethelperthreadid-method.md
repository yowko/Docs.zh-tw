---
title: "ICorDebugProcess::GetHelperThreadID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHelperThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 092e99cb1d5534cee56db08b5a2eedaaa2fc4724
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="4aa7b-102">ICorDebugProcess::GetHelperThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="4aa7b-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="4aa7b-103">取得偵錯工具的內部協助程式執行緒的作業系統 (OS) 執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aa7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4aa7b-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4aa7b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4aa7b-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="4aa7b-106">[out]指向 OS 執行緒偵錯工具的內部協助程式執行緒的 ID。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4aa7b-107">備註</span><span class="sxs-lookup"><span data-stu-id="4aa7b-107">Remarks</span></span>  
 <span data-ttu-id="4aa7b-108">Managed 和 unmanaged 偵錯期間，是以確保具有指定識別碼的執行緒保持執行，如果叫用中斷點放在偵錯工具偵錯工具的責任。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="4aa7b-109">偵錯工具可能也想要隱藏使用者從這個執行緒。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="4aa7b-110">如果沒有協助程式執行緒存在於處理程序，`GetHelperThreadID`方法會傳回零 *`pThreadID`。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in *`pThreadID`.</span></span>  
  
 <span data-ttu-id="4aa7b-111">因為它會隨著時間變更，無法快取，在協助程式執行緒的執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="4aa7b-112">您必須重新查詢在每個停止事件的執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="4aa7b-113">偵錯工具 helper 執行緒的執行緒 ID 將會是正確的每個 unmanaged [icordebugmanagedcallback:: Createthread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)事件，如此可讓偵錯工具若要判斷其協助程式執行緒的執行緒 ID 和隱藏使用者。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="4aa7b-114">被視為期間未受管理的協助程式執行緒的執行緒`ICorDebugManagedCallback::CreateThread`事件永遠不會執行 managed 的使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aa7b-115">需求</span><span class="sxs-lookup"><span data-stu-id="4aa7b-115">Requirements</span></span>  
 <span data-ttu-id="4aa7b-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aa7b-117">**標頭：** CorDebug.idl。</span><span class="sxs-lookup"><span data-stu-id="4aa7b-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="4aa7b-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4aa7b-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="4aa7b-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4aa7b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4aa7b-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aa7b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
