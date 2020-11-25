---
title: ICorDebugType::EnumerateTypeParameters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
ms.openlocfilehash: 3717497ab6e72f0ce67f688813ee7264206e8c84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727948"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters 方法

取得 ICorDebugTypeEnum 的介面指標，其中包含 <xref:System.Type> 這個 ICorDebugType 所參考之類別的參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppTyParEnum`  
 擴展的位址指標 `ICorDebugTypeEnum` ，其中包含類型的參數。  
  
## <a name="remarks"></a>備註  

 您可以使用， `EnumerateTypeParameters` 如果 [ICorDebugType：： GetType](icordebugtype-gettype-method.md) 傳回的 CorElementType 值為 ELEMENT_TYPE_CLASS、ELEMENT_TYPE_VALUETYPE、ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_FNPTR。 參數的數目及其順序取決於類型：  
  
- ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE：這個方法所傳回之的型別參數數目 `ICorDebugTypeEnum` ，將取決於對應類別的正式型別參數數目。 例如，如果類型為 `class Dict<String,int32>` ，則會傳回， `EnumerateTypeParameters` `ICorDebugTypeEnum` 其中包含代表 `String` 和順序的物件 `int32` 。  
  
- ELEMENT_TYPE_FNPTR：所包含的型別參數數目將會大於函式 `ICorDebugTypeEnum` 接受的引數數目。 包含在中的第一個型別參數是函式 `ICorDebugTypeEnum` 的傳回型別，而後續的型別參數則是函數的參數。  
  
- ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR：將會傳回一個類型參數。 例如，如果類型是陣列類型（例如 `int32[]` ）， `EnumerateTypeParameters` 則會傳回， `ICorDebugTypeEnum` 其中包含代表的物件 `int32` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
