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
ms.openlocfilehash: 55888786fdd8ff2b1d5610a74ee729db0d4fcfde
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976248"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue 方法
建立指定類型的值，其初始值為零或 null。  
  
 這個方法在 .NET Framework 版本2.0 中已過時。 請改用[ICorDebugEval2：： CreateValueForType](icordebugeval2-createvaluefortype-method.md) 。  
  
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
 在[CorElementType](../metadata/corelementtype-enumeration.md)列舉的值，指定值的類型。  
  
 `pElementClass`  
 在如果類型不是基本型別，則為指定值之類別的[ICorDebugClass](icordebugclass-interface.md)物件指標。  
  
 `ppValue`  
 脫銷表示值之 "ICorDebugValue" 物件位址的指標。  
  
## <a name="remarks"></a>備註  
 `CreateValue`針對在`ICorDebugValue`函數評估中使用的唯一目的，建立指定類型的物件。 這個值物件可以用來傳遞使用者常數做為參數。  
  
 如果值的類型是基本類型，其初始值為零或 null。 請使用[ICorDebugGenericValue：： SetValue](icordebuggenericvalue-setvalue-method.md)來設定基本類型的值。  
  
 如果 ELEMENT_TYPE_CLASS 的值`elementType` ，您會取得代表 null 物件參考的 "ICorDebugReferenceValue" `ppValue`（在中傳回）。 您可以使用這個物件，將 null 傳遞給具有物件參考參數的函式評估。 您不能將`ICorDebugValue`設定為任何專案;它一律會保持為 null。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1。0  
  
## <a name="see-also"></a>另請參閱

- [CreateValueForType 方法](icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval 介面](icordebugeval-interface.md)
