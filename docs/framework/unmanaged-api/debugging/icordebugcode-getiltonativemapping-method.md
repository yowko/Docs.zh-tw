---
title: ICorDebugCode::GetILToNativeMapping 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 011da6aacbf4c40420329952f47b1fabdfc2c1a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125625"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping 方法
取得 "COR_DEBUG_IL_TO_NATIVE_MAP" 實例的陣列，代表從 Microsoft 中繼語言（MSIL）位移到原生位移的對應。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `cMap`  
 [in] `map` 陣列的大小。  
  
 `pcMap`  
 脫銷`map` 陣列中所傳回之實際專案數目的指標。  
  
 `map`  
 脫銷`COR_DEBUG_IL_TO_NATIVE_MAP` 結構的陣列，其中每一個都代表從 MSIL 位移到原生位移的對應。  
  
 不會對傳回的元素陣列進行排序。  
  
## <a name="remarks"></a>備註  
 只有當這個 "ICorDebugCode" 實例代表從 MSIL 程式碼編譯而來的機器碼（JIT）時，`GetILToNativeMapping` 方法才會傳回有意義的結果。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugCode 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
