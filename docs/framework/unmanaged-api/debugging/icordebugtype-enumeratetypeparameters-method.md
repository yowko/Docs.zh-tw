---
title: "ICorDebugType::EnumerateTypeParameters 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9dd00b0a5f28821112621a54c97551c71e1acc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters 方法
取得包含 ICorDebugTypeEnum 介面指標<xref:System.Type>此 ICorDebugType 所參考類別的參數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppTyParEnum`  
 [out]位址指標`ICorDebugTypeEnum`包含類型的參數。  
  
## <a name="remarks"></a>備註  
 您可以使用`EnumerateTypeParameters`如果 CorElementType 值傳回[icordebugtype:: Gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) ELEMENT_TYPE_CLASS、 ELEMENT_TYPE_VALUETYPE、 ELEMENT_TYPE_ARRAY、 ELEMENT_TYPE_SZARRAY、 ELEMENT_TYPE_BYREF、 ELEMENT_TYPE_PTR 或 ELEMENT_TYPE_FNPTR。 參數數目和它們的順序取決於類型：  
  
-   ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE： 中所包含的型別參數數目`ICorDebugTypeEnum`，此方法傳回時，將取決於對應的類別的型式型別參數數目。 例如，如果類型是`class Dict<String,int32>`，然後`EnumerateTypeParameters`會傳回`ICorDebugTypeEnum`，其中包含代表物件`String`和`int32`序列中。  
  
-   ELEMENT_TYPE_FNPTR: 中所包含的類型參數的數目`ICorDebugTypeEnum`將會大於函式接受引數數目。 中所包含的第一個型別參數`ICorDebugTypeEnum`函數的傳回型別，而後續的型別參數是函式的參數。  
  
-   ELEMENT_TYPE_ARRAY、 ELEMENT_TYPE_SZARRAY、 ELEMENT_TYPE_BYREF 或 ELEMENT_TYPE_PTR： 將會傳回一個型別參數。 例如，如果類型是陣列類型，例如`int32[]`，`EnumerateTypeParameters`會傳回`ICorDebugTypeEnum`，其中包含物件，代表`int32`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
