---
title: ICorDebugComObjectValue::GetCachedInterfacePointers 方法
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77e7f20aba1908a63d77b4ccada7fabacf55f7
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025857"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers 方法
取得目前執行階段可呼叫包裝函式 (RCW) 上快取的原始介面指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>參數  
 `bIInspectableOnly`  
 [in]值，指出是否此方法會傳回唯一的 Windows 執行階段介面 (`IInspectable`介面) 或所快取的執行階段可呼叫包裝函式 (RCW) 的所有 COM 介面。  
  
 `celt`  
 [in]其位址是要擷取的物件數目。  
  
 `pceltFetched`  
 [out]指標的數目`CORDB_ADDRESS`中實際傳回的值`ptrs`。  
  
 `ptrs`  
 陣列的起始位址的指標`CORDB_ADDRESS`快取的值，包含位址之介面的物件。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugComObjectValue 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
