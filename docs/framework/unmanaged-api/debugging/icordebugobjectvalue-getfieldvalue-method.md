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
ms.openlocfilehash: 745be25183f6b94e7a807c4230961d72e2836fe5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695331"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue 方法

取得這個物件值之指定類別的指定域值。  
  
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
 在"ICorDebugClass" 物件的指標，代表要取得其域值的類別。  
  
 `fieldDef`  
 在 `mdFieldDef` 參考描述欄位之中繼資料的權杖。  
  
 `ppValue`  
 擴展代表指定之欄位值的 "ICorDebugValue" 物件指標。  
  
## <a name="remarks"></a>備註  

 參數中指定的類別 `pClass` 必須在物件值的類別階層中，而且欄位必須是該類別的欄位。  
  
 `GetFieldValue`泛型物件和泛型類別的方法仍然會成功。 例如，如果 MyDictionary \<V> 繼承自字典 \<string,V> ，而物件值的類型是 MyDictionary，則 \<int32> 傳遞字典的 `ICorDebugClass` 物件 \<K,V> 將會成功取得字典的欄位 \<string,int32> 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
