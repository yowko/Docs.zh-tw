---
title: ICorDebugProcess::ClearCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: b8d20de990ff4a27a82590342494a307c986457e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207399"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="c4b09-102">ICorDebugProcess::ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="c4b09-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="c4b09-103">清除指定執行緒上目前的非受控例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4b09-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b09-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4b09-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4b09-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4b09-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c4b09-106">在將清除目前非受控例外狀況之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c4b09-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b09-107">備註</span><span class="sxs-lookup"><span data-stu-id="c4b09-107">Remarks</span></span>  
 <span data-ttu-id="c4b09-108">呼叫這個方法，然後線上程已報告不應由偵錯工具忽略的非受控例外狀況時，再呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="c4b09-108">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="c4b09-109">這會清除指定執行緒上的未處理頻外（IB）和頻外（OOB）事件。</span><span class="sxs-lookup"><span data-stu-id="c4b09-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="c4b09-110">系統會自動清除所有 OOB 中斷點和單一步驟的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4b09-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="c4b09-111">請使用[ICorDebugThread2：： InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md)來攔截執行緒上目前的 managed 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c4b09-111">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b09-112">需求</span><span class="sxs-lookup"><span data-stu-id="c4b09-112">Requirements</span></span>  
 <span data-ttu-id="c4b09-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4b09-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b09-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4b09-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4b09-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4b09-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4b09-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b09-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
