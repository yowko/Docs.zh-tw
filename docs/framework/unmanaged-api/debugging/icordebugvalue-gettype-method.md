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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fc0dd03abc1adb8eeea76a1053fb4d58de4ecf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType 方法
取得這個 「 ICorDebugValue 」 物件的基本類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pType`  
 [out]值為"CorElementType 」 列舉值，指出值的類型指標。  
  
## <a name="remarks"></a>備註  
 如果物件是複雜的執行階段類型，該類型可以透過適當的子類別檢查`ICorDebugValue`介面。 例如，"ICorDebugObjectValue 」，以繼承自`ICorDebugValue`，表示複雜類型。  
  
 `GetType`和[icordebugobjectvalue:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)方法都會傳回值的類型資訊。 它們會同時取代感知泛型[icordebugvalue2:: Getexacttype](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 
