---
title: ICorDebugProcess5::GetTypeFields 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c2725c62105e92996bb2d8e79e8ff504904e9c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107948"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields 方法
提供屬於型別欄位的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>參數  
 `id`  
 [in]會擷取其欄位資訊類型的識別碼。  
  
 `celt`  
 [in]數目[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)其欄位資訊是要擷取的物件。  
  
 `fields`  
 [out]陣列[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)提供屬於型別欄位的相關資訊的物件。  
  
 `pceltNeeded`  
 [out]指標的數目[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)中所包含物件`fields`。  
  
## <a name="remarks"></a>備註  
 `celt`參數，指定欄位的方法用來填入其欄位資訊數目`fields`，應該會對應至值`COR_TYPE_LAYOUT::numFields`欄位。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugProcess5 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
