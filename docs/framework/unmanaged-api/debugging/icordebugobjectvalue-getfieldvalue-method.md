---
title: ICorDebugObjectValue::GetFieldValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
ms.openlocfilehash: 002c6cccb3ddf29b831ba5e14baa5e51f1b82433
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095886"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue 方法
取得這個物件值的指定類別之指定欄位的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `pClass`  
 在"ICorDebugClass" 物件的指標，代表要取得域值的類別。  
  
 `fieldDef`  
 在參考描述欄位之中繼資料的 `mdFieldDef` token。  
  
 `ppValue`  
 脫銷代表指定欄位之值的 "ICorDebugValue" 物件指標。  
  
## <a name="remarks"></a>備註  
 在 `pClass` 參數中指定的類別必須在物件值類別的階層中，而且該欄位必須是該類別的欄位。  
  
 泛型物件和泛型類別的 `GetFieldValue` 方法仍然會成功。 例如，如果 MyDictionary\<V > 繼承自字典\<string，V >，而且物件值的類型是 MyDictionary\<int32 >，則會傳遞字典的 `ICorDebugClass` 物件\<K，V > 會成功取得的欄位字典\<字串，int32 >。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱
