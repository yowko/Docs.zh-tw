---
title: ICorDebugThread::GetID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11e21e913e4749705ba6c7f91016be21b4de1712
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769976"
---
# <a name="icordebugthreadgetid-method"></a>ICorDebugThread::GetID 方法
取得目前的作業系統識別項的使用中的這個 ICorDebugThread 部分。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a>參數  
 `pdwThreadId`  
 [out]執行緒的識別碼。  
  
## <a name="remarks"></a>備註  
 作業系統識別項期間執行的處理序中，有可能變更，而且可以是不同的值不同部分的執行緒。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
