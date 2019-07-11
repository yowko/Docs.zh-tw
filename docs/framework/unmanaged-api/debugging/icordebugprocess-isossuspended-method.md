---
title: ICorDebugProcess::IsOSSuspended 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755468"
---
# <a name="icordebugprocessisossuspended-method"></a><span data-ttu-id="42e52-102">ICorDebugProcess::IsOSSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="42e52-102">ICorDebugProcess::IsOSSuspended Method</span></span>
<span data-ttu-id="42e52-103">取得值，指出指定的執行緒是否已暫停偵錯工具停止此程序的結果。</span><span class="sxs-lookup"><span data-stu-id="42e52-103">Gets a value that indicates whether the specified thread has been suspended as a result of the debugger stopping this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42e52-104">語法</span><span class="sxs-lookup"><span data-stu-id="42e52-104">Syntax</span></span>  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42e52-105">參數</span><span class="sxs-lookup"><span data-stu-id="42e52-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="42e52-106">[in]有問題的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="42e52-106">[in] The ID of thread in question.</span></span>  
  
 `pbSuspended`  
 <span data-ttu-id="42e52-107">[out]布林值的指標`true`如果指定的執行緒已經暫止，否則為 \*`pbSuspended`是`false`。</span><span class="sxs-lookup"><span data-stu-id="42e52-107">[out] A pointer to a Boolean value that is `true` if the specified thread has been suspended; otherwise \*`pbSuspended` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42e52-108">備註</span><span class="sxs-lookup"><span data-stu-id="42e52-108">Remarks</span></span>  
 <span data-ttu-id="42e52-109">指定的執行緒的 Win32 時指定的執行緒已暫停偵錯工具停止此程序的結果，暫停計數會遞增 1。</span><span class="sxs-lookup"><span data-stu-id="42e52-109">When the specified thread has been suspended as a result of the debugger stopping this process, the specified thread's Win32 suspend count is incremented by one.</span></span> <span data-ttu-id="42e52-110">偵錯工具使用者介面 (UI) 可能想要讓這項資訊列入考量，如果它會顯示作業系統 (OS) 暫止的執行緒給使用者的計數。</span><span class="sxs-lookup"><span data-stu-id="42e52-110">The debugger user interface (UI) may want to take this information into account if it displays the operating system (OS) suspend count of the thread to the user.</span></span>  
  
 <span data-ttu-id="42e52-111">`IsOSSuspended`方法有意義的非受控偵錯內容中。</span><span class="sxs-lookup"><span data-stu-id="42e52-111">The `IsOSSuspended` method makes sense only in the context of unmanaged debugging.</span></span> <span data-ttu-id="42e52-112">Managed 偵錯期間，執行緒是以合作方式暫止而不是不是 OS 暫止。</span><span class="sxs-lookup"><span data-stu-id="42e52-112">During managed debugging, threads are cooperatively suspended rather than OS-suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42e52-113">需求</span><span class="sxs-lookup"><span data-stu-id="42e52-113">Requirements</span></span>  
 <span data-ttu-id="42e52-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42e52-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42e52-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42e52-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42e52-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42e52-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42e52-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42e52-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
