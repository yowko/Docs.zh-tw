---
title: COR_DEBUG_IL_TO_NATIVE_MAP 結構
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
ms.openlocfilehash: 2a36c9808f29c038e3185157078c235959baf13c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132371"
---
# <a name="cor_debug_il_to_native_map-structure"></a>COR_DEBUG_IL_TO_NATIVE_MAP 結構
包含用來將 Microsoft 中繼語言 (MSIL) 程式碼對應至機器碼的位移。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`ilOffset`|MSIL 程式碼的位移。|  
|`nativeStartOffset`|機器碼開頭的位移。|  
|`nativeEndOffset`|機器碼結尾的位移。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl，Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetILToNativeMapping 方法](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [GetILToNativeMapping 方法](icordebugcode-getiltonativemapping-method.md)
- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
