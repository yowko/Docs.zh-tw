---
title: ICorDebugEval::CreateValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0af820b590271e16cbfb443c193fd0afb4ed3358
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604104"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue 方法
建立具有的值指定的類型，初始值為零或 null。  
  
 這個方法是在.NET Framework 2.0 版中已過時。 使用[ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)改。  
  
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
 [in]指標[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)物件，如果類型不是基本型別指定值的類別。  
  
 `ppValue`  
 [out]表示值的"ICorDebugValue 」 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 `CreateValue` 建立`ICorDebugValue`用途使用函式評估中的指定型別的物件。 此值物件可用來做為參數傳遞使用者常數。  
  
 如果值的型別是基本型別，其初始值為零，則為 null。 使用[icordebuggenericvalue:: Setvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)設定基本類型的值。  
  
 如果值`elementType`是 ELEMENT_TYPE_CLASS，取得"ICorDebugReferenceValue 」 (傳入`ppValue`) 代表 null 物件參考。 您可以使用這個物件將 null 傳遞至函式評估的物件參考參數。 您不能設定`ICorDebugValue`到任何項目，它一定會保持為 null。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1, 1.0  
  
## <a name="see-also"></a>另請參閱

- [CreateValueForType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)ICorDebugValue
