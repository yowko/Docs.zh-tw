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
ms.openlocfilehash: 11acf997b2efd74bc8394d830f36d3acbd1eef56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137205"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="f854c-102">ICorDebugProcess2::GetThreadForTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="f854c-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="f854c-103">取得具有指定識別碼之工作執行所在的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f854c-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f854c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f854c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f854c-105">參數</span><span class="sxs-lookup"><span data-stu-id="f854c-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="f854c-106">在工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f854c-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="f854c-107">脫銷ICorDebugThread2 物件位址的指標，代表要抓取的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f854c-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f854c-108">備註</span><span class="sxs-lookup"><span data-stu-id="f854c-108">Remarks</span></span>  
 <span data-ttu-id="f854c-109">主機可以使用[ICLRTask：： SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)方法來設定工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="f854c-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f854c-110">需求</span><span class="sxs-lookup"><span data-stu-id="f854c-110">Requirements</span></span>  
 <span data-ttu-id="f854c-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f854c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f854c-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f854c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f854c-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f854c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f854c-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f854c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
