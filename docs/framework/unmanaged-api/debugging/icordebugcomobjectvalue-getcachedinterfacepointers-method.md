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
ms.openlocfilehash: c1e2b557a5e5794c50986b1af8ec39faba845cc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125508"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers 方法
取得在目前執行時間可呼叫包裝函式（RCW）上快取的原始介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a>參數  
 `bIInspectableOnly`  
 在值，指出此方法是否只會傳回 Windows 執行階段介面（`IInspectable` 介面）或由執行時間可呼叫包裝函式（RCW）所快取的所有 COM 介面。  
  
 `celt`  
 在要抓取其位址的物件數目。  
  
 `pceltFetched`  
 脫銷`ptrs`中實際傳回之 `CORDB_ADDRESS` 值數目的指標。  
  
 `ptrs`  
 `CORDB_ADDRESS` 值陣列的起始位址指標，其中包含快取介面物件的位址。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugComObjectValue 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
