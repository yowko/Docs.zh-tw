---
title: "ICorDebugProcess::GetThreadContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e45d101db946747463ba4200bc5dd3b95d21391
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="c5471-102">ICorDebugProcess::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="c5471-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="c5471-103">取得這個處理程序中指定之執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="c5471-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5471-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5471-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5471-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5471-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c5471-106">[in]要擷取的內容執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5471-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c5471-107">[in] `context` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="c5471-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="c5471-108">[in、 out]描述執行緒的內容的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c5471-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="c5471-109">內容指定在執行緒上執行的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="c5471-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5471-110">備註</span><span class="sxs-lookup"><span data-stu-id="c5471-110">Remarks</span></span>  
 <span data-ttu-id="c5471-111">偵錯工具應該呼叫這個方法，而不是 Win32`GetThreadContext`方法，因為執行緒實際上可能處於 「 被盜用 」 狀態中, 其內容已暫時變更。</span><span class="sxs-lookup"><span data-stu-id="c5471-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="c5471-112">只有在執行緒處於原生程式碼時，應該使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="c5471-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="c5471-113">使用[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) managed 程式碼中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c5471-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="c5471-114">傳回的資料是目前的平台的內容結構。</span><span class="sxs-lookup"><span data-stu-id="c5471-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="c5471-115">如同 Win32`GetThreadContext`方法，呼叫端應該初始化`context`之前呼叫這個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="c5471-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5471-116">需求</span><span class="sxs-lookup"><span data-stu-id="c5471-116">Requirements</span></span>  
 <span data-ttu-id="c5471-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5471-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5471-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5471-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5471-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5471-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5471-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5471-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
