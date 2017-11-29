---
title: "ICorDebugThread2::GetTaskID 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetTaskID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e2d5a845b7047949618bed4176e6d24fee43c14
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="3db8c-102">ICorDebugThread2::GetTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="3db8c-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="3db8c-103">取得此執行緒上執行之工作的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3db8c-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db8c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3db8c-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3db8c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3db8c-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="3db8c-106">[out]這個 ICorDebugThread2 物件代表在執行緒上執行工作的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="3db8c-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3db8c-107">備註</span><span class="sxs-lookup"><span data-stu-id="3db8c-107">Remarks</span></span>  
 <span data-ttu-id="3db8c-108">工作只在執行緒上執行，如果執行緒與連接相關聯。</span><span class="sxs-lookup"><span data-stu-id="3db8c-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="3db8c-109">`GetTaskID`在中，則傳回零`pTaskId`如果執行緒目前無法與連接相關聯。</span><span class="sxs-lookup"><span data-stu-id="3db8c-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db8c-110">需求</span><span class="sxs-lookup"><span data-stu-id="3db8c-110">Requirements</span></span>  
 <span data-ttu-id="3db8c-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3db8c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db8c-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3db8c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3db8c-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3db8c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3db8c-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db8c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
