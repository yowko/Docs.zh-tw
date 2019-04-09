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
ms.openlocfilehash: 83265c4f6dffed76f1710378cf5293aac7020ef2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119349"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType 方法
取得這個 「 ICorDebugValue"物件的基本類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>參數  
 `pType`  
 [out]值為"CorElementType"列舉，指出值的類型指標。  
  
## <a name="remarks"></a>備註  
 如果物件是複雜的執行階段型別，該類型會檢查透過適當的子`ICorDebugValue`介面。 例如，"ICorDebugObjectValue 」，繼承自`ICorDebugValue`，表示複雜型別。  
  
 `GetType`並[icordebugobjectvalue:: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)方法都會傳回值的型別資訊。 它們兩者都由取代感知泛型[ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
