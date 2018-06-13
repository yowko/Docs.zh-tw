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
ms.openlocfilehash: f5690856b526bf0f7bc4527d04ae8044cda1f6e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417862"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID 方法
取得此執行緒上執行之工作的識別碼。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pTaskId`  
 [out]這個 ICorDebugThread2 物件代表在執行緒上執行工作的識別碼指標。  
  
## <a name="remarks"></a>備註  
 工作只在執行緒上執行，如果執行緒與連接相關聯。 `GetTaskID` 在中，則傳回零`pTaskId`如果執行緒目前無法與連接相關聯。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
