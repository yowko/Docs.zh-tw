---
title: ICorDebugRegisterSet::GetRegistersAvailable 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d600b4687b86f5872f94a60ad3422be764cf5307
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747214"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a>ICorDebugRegisterSet::GetRegistersAvailable 方法
取得位元遮罩，指出其會登錄在此[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)目前可用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a>參數  
 `pAvailable`  
 [out]位元遮罩，指出目前使用哪些暫存器。  
  
## <a name="remarks"></a>備註  
 暫存器可能無法使用，如果其值無法判斷指定的情況。  
  
 傳回的遮罩位元包含每個暫存器 (1 << 暫存索引)。 位元值為 1，如果將暫存器可供使用，則為 0，如果它無法使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugRegisterSet 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
