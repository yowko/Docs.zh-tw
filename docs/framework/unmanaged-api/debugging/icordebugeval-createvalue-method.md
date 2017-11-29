---
title: "ICorDebugEval::CreateValue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CreateValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7242e98a69083ca8d5a6d8d54e9b25279abb7bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue 方法
建立指定類型的值，其初始值為零或 null。  
  
 這個方法是.NET Framework 2.0 版中已過時。 使用[icordebugeval2:: Createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)改為。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `elementType`  
 [in]值為[CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md)列舉，指定值的類型。  
  
 `pElementClass`  
 [in]指標[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)物件，指定類別的值，如果型別不是 primitive 類型。  
  
 `ppValue`  
 [out]表示值的"ICorDebugValue 」 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 `CreateValue`建立`ICorDebugValue`只是為了在使用中函式評估的指定型別的物件。 此值的物件可以用來做為參數傳遞使用者常數。  
  
 如果值的型別是基本型別，其初始值為零，則為 null。 使用[icordebuggenericvalue:: Setvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)設定基本類型的值。  
  
 如果值`elementType`是 ELEMENT_TYPE_CLASS，取得"ICorDebugReferenceValue 」 (傳回`ppValue`) 代表 null 物件的參考。 您可以使用這個物件將 null 傳遞至具有物件參考參數的函式評估。 您不能設定`ICorDebugValue`到任何項目，它一定會保持為 null。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1、 1.0  
  
## <a name="see-also"></a>另請參閱  
    
 [CreateValueForType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 ICorDebugValue
