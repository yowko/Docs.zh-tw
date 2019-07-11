---
title: ICorDebugILFrame2::EnumerateTypeParameters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2e53bfb46579cc51b7ad88ef7de2b9f8d2f9390
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758764"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters 方法
取得包含 ICorDebugTypeEnum 物件<xref:System.Type>這個框架中的參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppTyParEnum`  
 ICorDebugTypeEnum 介面物件，可讓列舉型別之型別參數的位址指標。  
  
 型別參數的清單中包含的類別型別參數 （如果有的話） 後接的方法類型參數 （如果有的話）。  
  
## <a name="remarks"></a>備註  
 使用[IMetaDataImport2::EnumGenericParams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)方法來判斷多少類別型別參數和方法型別這份清單包含的參數。  
  
 型別參數不一定可用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
