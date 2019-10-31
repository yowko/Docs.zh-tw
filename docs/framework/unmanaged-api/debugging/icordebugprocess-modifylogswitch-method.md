---
title: ICorDebugProcess::ModifyLogSwitch 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
ms.openlocfilehash: 86b8737577bdb5f61f1061cb217620fae03ebd0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139381"
---
# <a name="icordebugprocessmodifylogswitch-method"></a>ICorDebugProcess::ModifyLogSwitch 方法
設定指定之記錄參數的嚴重性層級。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a>參數  
 `pLogSwitchName`  
 在字串的指標，指定記錄參數的名稱。  
  
 `lLevel`  
 在要為指定的記錄參數設定的嚴重性層級。  
  
## <a name="remarks"></a>備註  
 只有在發生[ICorDebugManagedCallback：： CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼時，這個方法才有效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
