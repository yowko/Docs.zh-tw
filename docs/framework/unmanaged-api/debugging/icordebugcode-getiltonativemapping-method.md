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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c30623e53b57a78287b26d4a362793cfb32baede
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131055"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>ICorDebugCode::GetILToNativeMapping 方法
取得"COR_DEBUG_IL_TO_NATIVE_MAP 」 執行個體，表示對應從 Microsoft intermediate language (MSIL) 位移到原生位移陣列。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [out]項目中傳回的實際數目的指標`map`陣列。  
  
 `map`  
 [out]陣列`COR_DEBUG_IL_TO_NATIVE_MAP`結構，每一個都代表從 MSIL 位移到原生位移的對應。  
  
 沒有任何排序傳回的項目的陣列。  
  
## <a name="remarks"></a>備註  
 `GetILToNativeMapping`方法會傳回有意義的結果，只有當此"ICorDebugCode 」 執行個體代表已在 just-in-time (JIT) 編譯的 MSIL 程式碼的原生程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugCode 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
