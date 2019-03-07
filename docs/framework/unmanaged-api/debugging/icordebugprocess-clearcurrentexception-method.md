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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f014f9213a4b9a2d5119af9a6dceebb9a9d54b52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473460"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="dcb13-102">ICorDebugProcess::ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="dcb13-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="dcb13-103">清除指定的執行緒上目前的 unmanaged 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dcb13-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb13-104">語法</span><span class="sxs-lookup"><span data-stu-id="dcb13-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcb13-105">參數</span><span class="sxs-lookup"><span data-stu-id="dcb13-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="dcb13-106">[in]將會清除目前的 unmanaged 例外狀況所在的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="dcb13-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcb13-107">備註</span><span class="sxs-lookup"><span data-stu-id="dcb13-107">Remarks</span></span>  
 <span data-ttu-id="dcb13-108">呼叫這個方法，然後再呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)執行緒時回報的未受管理的例外狀況，偵錯項目應該予以忽略。</span><span class="sxs-lookup"><span data-stu-id="dcb13-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="dcb13-109">這會清除未完成-頻外 (IB) 和指定的執行緒上的頻外 (OOB) 事件。</span><span class="sxs-lookup"><span data-stu-id="dcb13-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="dcb13-110">自動清除所有的 OOB 中斷點和逐步執行例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dcb13-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="dcb13-111">使用[ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)攔截目前 managed 執行緒上的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dcb13-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcb13-112">需求</span><span class="sxs-lookup"><span data-stu-id="dcb13-112">Requirements</span></span>  
 <span data-ttu-id="dcb13-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dcb13-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcb13-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcb13-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcb13-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcb13-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcb13-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcb13-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
