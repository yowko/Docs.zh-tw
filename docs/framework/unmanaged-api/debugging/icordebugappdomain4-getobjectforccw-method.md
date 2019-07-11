---
title: ICorDebugAppDomain4::GetObjectForCCW 方法
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ab4905c55a1395e9ae5cba8343e6b832622005d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737637"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a>ICorDebugAppDomain4::GetObjectForCCW 方法
從 COM 可呼叫包裝函式 (CCW) 指標取得 Managed 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `ccwPointer`  
 [in] COM 可呼叫包裝函式 (CCW) 指標。  
  
 `ppManagedObject`  
 [out]「 ICorDebugValue 」 物件，表示受管理的物件，其對應到指定 CCW 指標的位址指標。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugAppDomain4 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
