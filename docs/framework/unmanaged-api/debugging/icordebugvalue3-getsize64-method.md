---
title: ICorDebugValue3::GetSize64 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96e63d121bb64fd1aa6433881f7806b5c4058115
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773995"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 方法
取得大小，以位元組為單位，這[ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>參數  
 pSize  
 [out]大小 （位元組），這個物件的指標。  
  
## <a name="remarks"></a>備註  
 如果此值的型別是參考型別，這個方法會傳回指標的大小，而不是物件的大小。  
  
 `ICorDebugValue3::GetSize`方法不同於[icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)其輸出參數的型別中的方法。 在  [icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)，輸出參數是`ULONG32`; 在`ICorDebugValue3::GetSize`，它是`ULONG64`。 這可讓[ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)介面來報告的大小超過 2 GB 的陣列。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugValue3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
