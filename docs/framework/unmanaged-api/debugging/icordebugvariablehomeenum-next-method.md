---
title: ICorDebugVariableHomeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be1ba87ae979911dd21647569725eafa2c80ffa6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768806"
---
# <a name="icordebugvariablehomeenumnext-method"></a>ICorDebugVariableHomeEnum::Next 方法
取得指定的數目[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)包含區域變數和函式中的引數的相關資訊的執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
 [in] 要擷取的物件數目。  
  
 `homes`  
 指標的陣列，其中每一個指向[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)提供的本機變數或函式的引數的相關資訊的物件。  
  
 `pceltFetched`  
 [out]物件中實際傳回的執行個體數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回下列值。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功完成命令。|  
|`S_FALSE`|擷取執行個體的實際數目，如中所反映`pceltFetched`，小於要求的執行個體數目。|  
  
## <a name="remarks"></a>備註  
 [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)方法會擷取最多`celt`列舉值目前位置開始的物件。 方法傳回時，`pceltFetched`包含的實際擷取的物件數目。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugVariableHomeEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
