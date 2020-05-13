---
title: ICorDebugProcess::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 2bdbf373144e2fb49074cfd035e7b0ffe3c8c291
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212881"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="8e3e4-102">ICorDebugProcess::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="8e3e4-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="8e3e4-103">取得這個進程中指定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e3e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e3e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e3e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e3e4-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="8e3e4-106">在要為其取得內容的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8e3e4-107">[in] `context` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="8e3e4-108">[in、out]描述執行緒內容的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="8e3e4-109">內容會指定執行緒在其上執行的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e3e4-110">備註</span><span class="sxs-lookup"><span data-stu-id="8e3e4-110">Remarks</span></span>  
 <span data-ttu-id="8e3e4-111">偵錯工具應該呼叫這個方法，而不是 Win32 `GetThreadContext` 方法，因為執行緒實際上可能處於「遭劫持」狀態，而其內容已暫時變更。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="8e3e4-112">只有線上程是機器碼時，才應該使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="8e3e4-113">針對 managed 程式碼中的執行緒使用[ICorDebugRegisterSet](icordebugregisterset-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="8e3e4-114">傳回的資料是目前平臺的內容結構。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="8e3e4-115">就像 Win32 方法一樣 `GetThreadContext` ，呼叫者應該在 `context` 呼叫這個方法之前先初始化參數。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e3e4-116">需求</span><span class="sxs-lookup"><span data-stu-id="8e3e4-116">Requirements</span></span>  
 <span data-ttu-id="8e3e4-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e3e4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e3e4-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e3e4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e3e4-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e3e4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e3e4-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e3e4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
