---
title: "ICorDebugProcess::SetThreadContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7d40d455ea17b8df2acd77a1222ac6b080116c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="d5cda-102">ICorDebugProcess::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="d5cda-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="d5cda-103">此程序中設定給定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="d5cda-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5cda-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5cda-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5cda-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5cda-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="d5cda-106">[in]這是要設定的內容執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d5cda-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d5cda-107">[in] `context` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="d5cda-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="d5cda-108">[in]描述執行緒的內容的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="d5cda-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="d5cda-109">內容指定在執行緒上執行的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="d5cda-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5cda-110">備註</span><span class="sxs-lookup"><span data-stu-id="d5cda-110">Remarks</span></span>  
 <span data-ttu-id="d5cda-111">偵錯工具應該呼叫這個方法，而不是 Win32`SetThreadContext`函式，因為執行緒實際上可能處於 「 被盜用 」 狀態中, 其內容已暫時變更。</span><span class="sxs-lookup"><span data-stu-id="d5cda-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="d5cda-112">只有在執行緒處於原生程式碼時，應該使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="d5cda-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="d5cda-113">使用[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) managed 程式碼中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="d5cda-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="d5cda-114">您應該永遠不需要修改期間的頻外 (OOB) 偵錯事件的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="d5cda-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="d5cda-115">傳遞的資料必須是目前的平台的內容結構。</span><span class="sxs-lookup"><span data-stu-id="d5cda-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="d5cda-116">如果不當使用，這個方法可能會損毀的執行階段。</span><span class="sxs-lookup"><span data-stu-id="d5cda-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5cda-117">需求</span><span class="sxs-lookup"><span data-stu-id="d5cda-117">Requirements</span></span>  
 <span data-ttu-id="d5cda-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5cda-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5cda-119">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5cda-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5cda-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5cda-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5cda-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5cda-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
