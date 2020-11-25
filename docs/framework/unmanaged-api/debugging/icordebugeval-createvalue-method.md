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
ms.openlocfilehash: 41db6ac00d8646651d0e8433d076c37af6020071
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696150"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue 方法

建立指定類型的值，其初始值為零或 null。  
  
 此方法在 .NET Framework 版本2.0 中已淘汰。 請改用 [ICorDebugEval2：： CreateValueForType](icordebugeval2-createvaluefortype-method.md) 。  
  
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
 在 [CorElementType](../metadata/corelementtype-enumeration.md) 列舉的值，指定值的類型。  
  
 `pElementClass`  
 在如果類型不是基本類型，則為指定值之類別的 [ICorDebugClass](icordebugclass-interface.md) 物件指標。  
  
 `ppValue`  
 擴展代表值的 "ICorDebugValue" 物件位址的指標。  
  
## <a name="remarks"></a>備註  

 `CreateValue` 針對在 `ICorDebugValue` 函數評估中使用它的唯一目的，建立指定型別的物件。 此值物件可以用來將使用者常數當做參數傳遞。  
  
 如果值的類型是基本類型，則其初始值為零或 null。 使用 [ICorDebugGenericValue：： SetValue](icordebuggenericvalue-setvalue-method.md) 設定基本類型的值。  
  
 如果 ELEMENT_TYPE_CLASS 的值 `elementType` ，您會在) 中取得傳回的 "ICorDebugReferenceValue" (， `ppValue` 表示 null 物件參考。 您可以使用此物件，將 null 傳遞給具有物件參考參數的函式評估。 您無法將設定為任何值， `ICorDebugValue` 它一律會維持 null。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.1、1。0  
  
## <a name="see-also"></a>另請參閱

- [CreateValueForType 方法](icordebugeval2-createvaluefortype-method.md)
- [ICorDebugEval 介面](icordebugeval-interface.md)
