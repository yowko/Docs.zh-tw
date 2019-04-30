---
title: ICorDebugThread2::GetTaskID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 417f99c2b9fa7e77f8696c27cb3929c92956c08c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946329"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="1d925-102">ICorDebugThread2::GetTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="1d925-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="1d925-103">取得這個執行緒上執行之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1d925-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d925-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d925-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d925-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d925-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="1d925-106">[out]在這個 ICorDebugThread2 物件所代表的執行緒上執行工作的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="1d925-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d925-107">備註</span><span class="sxs-lookup"><span data-stu-id="1d925-107">Remarks</span></span>  
 <span data-ttu-id="1d925-108">工作只有在執行緒上執行，如果執行緒與連接相關聯。</span><span class="sxs-lookup"><span data-stu-id="1d925-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="1d925-109">`GetTaskID` 在中，則傳回零`pTaskId`如果執行緒目前無法與連線相關聯。</span><span class="sxs-lookup"><span data-stu-id="1d925-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d925-110">需求</span><span class="sxs-lookup"><span data-stu-id="1d925-110">Requirements</span></span>  
 <span data-ttu-id="1d925-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d925-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d925-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d925-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d925-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d925-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d925-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d925-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
