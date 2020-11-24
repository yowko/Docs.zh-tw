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
ms.openlocfilehash: 0adb9e58ca2c6b5b430a0413fa11ba59d79a0539
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688103"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping 方法

取得 "COR_DEBUG_IL_TO_NATIVE_MAP" 實例的陣列，這些實例表示從 Microsoft 中繼語言 (MSIL 到原生位移) 位移的對應。  
  
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
 擴展陣列中傳回的實際專案數目的指標 `map` 。  
  
 `map`  
 擴展結構的陣列 `COR_DEBUG_IL_TO_NATIVE_MAP` ，其中每一個都代表從 MSIL 位移到原生位移的對應。  
  
 傳回的元素陣列沒有順序。  
  
## <a name="remarks"></a>備註  

 `GetILToNativeMapping`只有當這個 "ICorDebugCode" 實例代表的原生程式碼是即時 (JIT) 從 MSIL 程式碼編譯時，方法才會傳回有意義的結果。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugCode 介面](icordebugcode-interface1.md)
