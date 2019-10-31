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
ms.openlocfilehash: d5f2838007504e56ad44614a6778083be046629f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140080"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID 方法
取得在這個執行緒上執行之工作的識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>參數  
 `pTaskId`  
 脫銷在這個 ICorDebugThread2 物件所代表的執行緒上執行之工作的識別碼指標。  
  
## <a name="remarks"></a>備註  
 工作只有線上程與連接相關聯時，才可以線上程上執行。 如果執行緒與連接沒有關聯，`GetTaskID` 會在 `pTaskId` 中傳回零。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
