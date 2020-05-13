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
ms.openlocfilehash: 841af546cc3586529fe290c69e686438f634b90d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377790"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="cc135-102">ICorDebugThread2::GetTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="cc135-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="cc135-103">取得在這個執行緒上執行之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cc135-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc135-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc135-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc135-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc135-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="cc135-106">脫銷在這個 ICorDebugThread2 物件所代表的執行緒上執行之工作的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="cc135-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc135-107">備註</span><span class="sxs-lookup"><span data-stu-id="cc135-107">Remarks</span></span>  
 <span data-ttu-id="cc135-108">工作只有線上程與連接相關聯時，才可以線上程上執行。</span><span class="sxs-lookup"><span data-stu-id="cc135-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="cc135-109">`GetTaskID``pTaskId`如果執行緒與連接沒有關聯，則會在中傳回零。</span><span class="sxs-lookup"><span data-stu-id="cc135-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc135-110">需求</span><span class="sxs-lookup"><span data-stu-id="cc135-110">Requirements</span></span>  
 <span data-ttu-id="cc135-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc135-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc135-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc135-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc135-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc135-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc135-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc135-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
