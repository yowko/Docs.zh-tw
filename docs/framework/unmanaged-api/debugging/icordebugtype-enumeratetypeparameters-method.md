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
ms.openlocfilehash: 57a82e4ec106fead105cc7f200e7e56026004328
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122374"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters 方法
取得 ICorDebugTypeEnum 的介面指標，其中包含這個 ICorDebugType 所參考之類別的 <xref:System.Type> 參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppTyParEnum`  
 脫銷包含型別參數之 `ICorDebugTypeEnum` 位址的指標。  
  
## <a name="remarks"></a>備註  
 如果[ICorDebugType：： GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)傳回的 CorElementType 值為 ELEMENT_TYPE_CLASS、ELEMENT_TYPE_VALUETYPE、ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_FNPTR，您就可以使用 `EnumerateTypeParameters`。 參數和其順序的數目取決於類型：  
  
- ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE：此方法所傳回之 `ICorDebugTypeEnum` 中包含的類型參數數目，將取決於對應類別的型式類型參數數目。 例如，如果類型是 `class Dict<String,int32>`，則 `EnumerateTypeParameters` 會傳回 `ICorDebugTypeEnum`，其中包含以序清單示 `String` 和 `int32` 的物件。  
  
- ELEMENT_TYPE_FNPTR： `ICorDebugTypeEnum` 中包含的型別參數數目會大於函數接受的引數數目。 `ICorDebugTypeEnum` 中所包含的第一個型別參數是函式的傳回型別，而後續的型別參數則是函數的參數。  
  
- ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR：將傳回一個型別參數。 例如，如果型別是陣列型別，例如 `int32[]`，`EnumerateTypeParameters` 會傳回一個 `ICorDebugTypeEnum`，其中包含代表 `int32`的物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
