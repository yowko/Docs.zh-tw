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
ms.openlocfilehash: 06f403f0b653866428a41240f99833ec1180eb86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731068"
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
 擴展"CorElementType" 列舉值的指標，指出值的類型。  
  
## <a name="remarks"></a>備註  

 如果物件是複雜的執行時間類型，則可以透過介面的適當子類別來檢查該類型 `ICorDebugValue` 。 例如，"ICorDebugObjectValue" （繼承自 `ICorDebugValue` ）代表複雜類型。  
  
 `GetType`和[ICorDebugObjectValue：： GetClass](icordebugobjectvalue-getclass-method.md)方法都會傳回值型別的相關資訊。 它們都是由具有泛型感知的 [ICorDebugValue2：： GetExactType](icordebugvalue2-getexacttype-method.md) 方法所取代。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
