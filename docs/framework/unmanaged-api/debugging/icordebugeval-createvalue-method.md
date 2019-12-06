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
ms.openlocfilehash: 4bb04ba090be9cab551bc39d8d9f1be974c747d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085141"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue 方法
建立指定類型的值，其初始值為零或 null。  
  
 這個方法在 .NET Framework 版本2.0 中已過時。 請改用[ICorDebugEval2：： CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `elementType`  
 在[CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md)列舉的值，指定值的類型。  
  
 `pElementClass`  
 在如果類型不是基本型別，則為指定值之類別的[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)物件指標。  
  
 `ppValue`  
 脫銷表示值之 "ICorDebugValue" 物件位址的指標。  
  
## <a name="remarks"></a>備註  
 `CreateValue` 會建立給定類型的 `ICorDebugValue` 物件，以在函數評估中使用它的唯一目的。 這個值物件可以用來傳遞使用者常數做為參數。  
  
 如果值的類型是基本類型，其初始值為零或 null。 請使用[ICorDebugGenericValue：： SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)來設定基本類型的值。  
  
 如果 `elementType` 的值為 ELEMENT_TYPE_CLASS，您會取得代表 null 物件參考的 "ICorDebugReferenceValue" （在 `ppValue`中傳回）。 您可以使用這個物件，將 null 傳遞給具有物件參考參數的函式評估。 您不能將 `ICorDebugValue` 設定為任何專案;它一律會保持為 null。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1.0  
  
## <a name="see-also"></a>請參閱

- [CreateValueForType 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval 介面](icordebugeval-interface.md)
