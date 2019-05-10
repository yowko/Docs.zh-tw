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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b48e375286e709a2ce570769c9a0453765824ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622681"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters 方法
取得包含 ICorDebugTypeEnum 介面指標<xref:System.Type>類別此 ICorDebugType 所參考的參數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppTyParEnum`  
 [out]位址指標`ICorDebugTypeEnum`包含類型的參數。  
  
## <a name="remarks"></a>備註  
 您可以使用`EnumerateTypeParameters`如果所傳回的 CorElementType 值[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS、 ELEMENT_TYPE_VALUETYPE、 ELEMENT_TYPE_ARRAY、 ELEMENT_TYPE_SZARRAY、 ELEMENT_TYPE_BYREF、 ELEMENT_TYPE_PTR,2001 年或 typ ELEMENT_TYPE_FNPTR。 參數數目和它們的順序取決於類型：  
  
- ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE:中所包含的型別參數數目`ICorDebugTypeEnum`，這個方法傳回時，將取決於對應的類別的型式的型別參數數目。 例如，如果類型是`class Dict<String,int32>`，然後`EnumerateTypeParameters`會傳回`ICorDebugTypeEnum`，其中包含物件，代表`String`和`int32`序列中。  
  
- TYP ELEMENT_TYPE_FNPTR:中所包含的型別參數數目`ICorDebugTypeEnum`會是其中一個大於函式所接受的引數數目。 第一個型別參數中包含`ICorDebugTypeEnum`是函式，傳回的型別，而後續的型別參數是函式的參數。  
  
- ELEMENT_TYPE_ARRAY、 ELEMENT_TYPE_SZARRAY、 ELEMENT_TYPE_BYREF，還是 ELEMENT_TYPE_PTR:會傳回一個型別參數。 例如，如果類型是陣列類型這類`int32[]`，`EnumerateTypeParameters`會傳回`ICorDebugTypeEnum`，其中包含這個物件代表`int32`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
