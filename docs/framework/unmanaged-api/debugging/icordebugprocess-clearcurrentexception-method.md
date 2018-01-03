---
title: "ICorDebugProcess::ClearCurrentException 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ClearCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905ade7e5c44861b4ad6e7eb57fe7d3e3e9e3002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="35a4a-102">ICorDebugProcess::ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="35a4a-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="35a4a-103">清除指定的執行緒上目前的 unmanaged 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35a4a-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a4a-104">語法</span><span class="sxs-lookup"><span data-stu-id="35a4a-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35a4a-105">參數</span><span class="sxs-lookup"><span data-stu-id="35a4a-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="35a4a-106">[in]將會清除目前的 unmanaged 例外狀況所在的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="35a4a-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35a4a-107">備註</span><span class="sxs-lookup"><span data-stu-id="35a4a-107">Remarks</span></span>  
 <span data-ttu-id="35a4a-108">呼叫這個方法之前先呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)執行緒時回報不受管理的例外狀況偵錯項目應該忽略。</span><span class="sxs-lookup"><span data-stu-id="35a4a-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="35a4a-109">這將會清除未完成頻外 (IB) 和指定的執行緒上的頻外 (OOB) 事件。</span><span class="sxs-lookup"><span data-stu-id="35a4a-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="35a4a-110">自動清除所有 OOB 中斷點和逐步執行例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35a4a-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="35a4a-111">使用[icordebugthread2:: Interceptcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)攔截目前受管理的執行緒上的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="35a4a-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a4a-112">需求</span><span class="sxs-lookup"><span data-stu-id="35a4a-112">Requirements</span></span>  
 <span data-ttu-id="35a4a-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35a4a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a4a-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35a4a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35a4a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35a4a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35a4a-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35a4a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
