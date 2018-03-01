---
title: "ICorDebugObjectValue::GetFieldValue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9fcf53610cf96ef1ab62b4768521e8a2fb7ee6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue 方法
取得指定類別的指定之欄位的值，這個物件值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pClass`  
 [in]表示要取得的欄位值的類別 」 ICorDebugClass 」 物件的指標。  
  
 `fieldDef`  
 [in]`mdFieldDef`參考描述欄位的中繼資料語彙基元。  
  
 `ppValue`  
 [out]代表指定之欄位的值"ICorDebugValue 」 物件的指標。  
  
## <a name="remarks"></a>備註  
 指定的類別`pClass`參數，必須是階層中的物件值的類別，而且此欄位必須是該類別的欄位。  
  
 `GetFieldValue`方法仍會成功的泛型物件和泛型類別。 例如，如果 MyDictionary\<V > 繼承自字典\<字串，V >，而且物件值的類型 MyDictionary\<int32 >，並傳遞`ICorDebugClass`字典的物件\<K，V > 將已順利取得欄位的字典\<字串、 int32 >。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
    
 
