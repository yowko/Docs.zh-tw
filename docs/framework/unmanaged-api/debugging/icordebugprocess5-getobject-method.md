---
title: ICorDebugProcess5::GetObject 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: 540ca78c5548d4fbdd3338671ea02314736f15cd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792368"
---
# <a name="icordebugprocess5getobject-method"></a>ICorDebugProcess5::GetObject 方法
將物件位址轉換成 "ICorDebugObjectValue" 物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `addr`  
 在物件位址。  
  
 `ppObject`  
 脫銷"ICorDebugObjectValue" 物件位址的指標。  
  
## <a name="remarks"></a>備註  
 如果 `addr` 未指向有效的 managed 物件，則 `GetObject` 方法會傳回 `E_FAIL`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess5 介面](icordebugprocess5-interface.md)
- [偵錯介面](debugging-interfaces.md)
