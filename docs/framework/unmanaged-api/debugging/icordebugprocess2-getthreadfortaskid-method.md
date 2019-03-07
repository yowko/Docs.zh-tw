---
title: ICorDebugProcess2::GetThreadForTaskID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa1f6852544dddcdf514b14710ade3949818c93e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487307"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="1600b-102">ICorDebugProcess2::GetThreadForTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="1600b-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="1600b-103">取得具有指定識別碼的工作執行所在的執行緒。</span><span class="sxs-lookup"><span data-stu-id="1600b-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1600b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1600b-104">Syntax</span></span>  
  
```  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1600b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1600b-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="1600b-106">[in]工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1600b-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="1600b-107">[out]ICorDebugThread2 物件，表示要擷取執行緒的位址指標。</span><span class="sxs-lookup"><span data-stu-id="1600b-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1600b-108">備註</span><span class="sxs-lookup"><span data-stu-id="1600b-108">Remarks</span></span>  
 <span data-ttu-id="1600b-109">主機可以透過設定的工作識別項[iclrtask:: Settaskidentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1600b-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1600b-110">需求</span><span class="sxs-lookup"><span data-stu-id="1600b-110">Requirements</span></span>  
 <span data-ttu-id="1600b-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1600b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1600b-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1600b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1600b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1600b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1600b-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1600b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
