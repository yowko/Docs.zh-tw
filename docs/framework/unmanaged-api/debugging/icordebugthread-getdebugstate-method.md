---
title: ICorDebugThread::GetDebugState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0baabbb736365b138d1754e68070207b4310bf57
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762455"
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState 方法
取得這個 ICorDebugThread 物件的目前偵錯狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a>參數  
 `pState`  
 [out]位元組合 CorDebugThreadState 列舉值，描述這個執行緒的目前偵錯狀態指標。  
  
## <a name="remarks"></a>備註  
 如果目前已停止處理程序，`pState`代表只存在於這個執行緒繼續執行，不實際目前執行緒的狀態這程序時的偵錯狀態。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
