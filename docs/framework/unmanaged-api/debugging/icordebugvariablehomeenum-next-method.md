---
title: ICorDebugVariableHomeEnum：： Next 方法
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
ms.openlocfilehash: 9c2c16789fb61099c9b7c58154810739d225af1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121927"
---
# <a name="icordebugvariablehomeenumnext-method"></a>ICorDebugVariableHomeEnum：： Next 方法
取得指定的[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)實例數目，其中包含函式中區域變數和引數的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 指標的陣列，其中每一個都會指向一個[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)物件，它會提供有關函數的區域變數或引數的資訊。  
  
 `pceltFetched`  
 脫銷物件中實際傳回的實例數目。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回下列值。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|`S_OK`|已成功完成命令。|  
|`S_FALSE`|如 `pceltFetched`所反映的實際實例數目，小於所要求的實例數目。|  
  
## <a name="remarks"></a>備註  
 [ICorDebugVariableHomeEnum：： Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)方法會從列舉值的目前位置開始，抓取 `celt` 物件的上限。 當此方法傳回時，`pceltFetched` 包含所抓取物件的實際數目。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugVariableHomeEnum 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
