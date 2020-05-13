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
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207585"
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
 在`mdFieldDef`參考描述欄位之中繼資料的 token。  
  
 `ppValue`  
 脫銷代表指定欄位之值的 "ICorDebugValue" 物件指標。  
  
## <a name="remarks"></a>備註  
 參數中指定的類別 `pClass` 必須在物件值類別的階層中，而且該欄位必須是該類別的欄位。  
  
 `GetFieldValue`泛型物件和泛型類別的方法仍然會成功。 例如，如果 MyDictionary \< v> 繼承自字典 \< 字串、V>，而且物件值的類型為 MyDictionary \< int32>，則傳遞 `ICorDebugClass` 字典 K 的物件， \< V> 將會成功取得字典 \< 字串 int32> 的欄位。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
