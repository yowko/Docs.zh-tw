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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8778edf9ac6e32d5dab3a53a6d9cc643a8df13b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107909"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue 方法
取得這個物件值，指定類別的指定欄位的值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `pClass`  
 [in]表示要取得的欄位值的類別 「 ICorDebugClass"物件的指標。  
  
 `fieldDef`  
 [in]`mdFieldDef`參考描述欄位的中繼資料語彙基元。  
  
 `ppValue`  
 [out]表示指定之欄位的值"ICorDebugValue 」 物件的指標。  
  
## <a name="remarks"></a>備註  
 中指定的類別`pClass`參數，必須是階層中的物件值的類別，且此欄位必須是該類別的欄位。  
  
 `GetFieldValue`方法仍然會成功的泛型物件的泛型類別。 比方說，如果 MyDictionary\<V > 繼承自字典\<字串，V >，而且物件值的類型 MyDictionary\<int32 >，並傳遞`ICorDebugClass`字典的物件\<K，V > 將已成功取得欄位的字典\<string，int32 >。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
