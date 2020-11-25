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
ms.openlocfilehash: 0d36390a905561b64b3ca6ca95722f82158450be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695214"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="f0f84-102">ICorDebugProcess::ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="f0f84-102">ICorDebugProcess::ClearCurrentException Method</span></span>

<span data-ttu-id="f0f84-103">清除指定執行緒上目前的非受控例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0f84-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f84-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0f84-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0f84-105">參數</span><span class="sxs-lookup"><span data-stu-id="f0f84-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="f0f84-106">在將清除目前非受控例外狀況之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f0f84-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0f84-107">備註</span><span class="sxs-lookup"><span data-stu-id="f0f84-107">Remarks</span></span>  

 <span data-ttu-id="f0f84-108">呼叫這個方法，然後再呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) （當執行緒已報告偵錯工具應該忽略的非受控例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="f0f84-108">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="f0f84-109">這會將未處理的頻外 (IB) ，以及指定執行緒上的頻外 (OOB) 事件清除。</span><span class="sxs-lookup"><span data-stu-id="f0f84-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="f0f84-110">系統會自動清除所有 OOB 中斷點和單一步驟例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0f84-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="f0f84-111">使用 [ICorDebugThread2：： InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) 攔截執行緒上目前的 managed 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0f84-111">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0f84-112">需求</span><span class="sxs-lookup"><span data-stu-id="f0f84-112">Requirements</span></span>  

 <span data-ttu-id="f0f84-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0f84-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0f84-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0f84-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0f84-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0f84-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0f84-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0f84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
