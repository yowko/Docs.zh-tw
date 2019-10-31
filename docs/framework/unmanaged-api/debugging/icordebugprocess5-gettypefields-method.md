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
ms.openlocfilehash: 0045285a3da22f468c2426bb3b9c4ae7e3e1d7c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132662"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields 方法
提供屬於類型之欄位的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>參數  
 `id`  
 在要抓取其欄位資訊之類型的識別碼。  
  
 `celt`  
 在要取出其欄位資訊的[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)物件數目。  
  
 `fields`  
 脫銷[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)物件的陣列，提供屬於該類型之欄位的相關資訊。  
  
 `pceltNeeded`  
 脫銷`fields`所包含之[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)物件數目的指標。  
  
## <a name="remarks"></a>備註  
 `celt` 參數，指定方法用來填入 `fields`之欄位資訊的欄位數目，應對應至 [`COR_TYPE_LAYOUT::numFields`] 欄位的值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess5 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
