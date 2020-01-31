---
title: ICorDebugValue::GetType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 7def2bd2c0f3ab501fdb918a0e9a7ee154159b78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791147"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType 方法
取得這個 "ICorDebugValue" 物件的基本類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>參數  
 `pType`  
 脫銷"CorElementType" 列舉值的指標，指出值的類型。  
  
## <a name="remarks"></a>備註  
 如果物件是複雜的執行時間類型，則可以透過 `ICorDebugValue` 介面的適當子類別來檢查該類型。 例如，"ICorDebugObjectValue" （繼承自 `ICorDebugValue`）代表複雜類型。  
  
 `GetType` 和[ICorDebugObjectValue：： GetClass](icordebugobjectvalue-getclass-method.md)方法都會傳回數值型別的相關資訊。 兩者都被泛型感知[ICorDebugValue2：： GetExactType](icordebugvalue2-getexacttype-method.md)方法所取代。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱
