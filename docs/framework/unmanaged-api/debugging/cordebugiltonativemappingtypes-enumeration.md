---
title: CorDebugIlToNativeMappingTypes 列舉
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: 808fc70a308eff1b05aa49ea2bb89fe53377c973
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795842"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a>CorDebugIlToNativeMappingTypes 列舉
指出特定的原生指令範圍（由 COR_DEBUG_IL_TO_NATIVE_MAP 結構的實例所表示）是否對應到特殊的程式碼區域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a>成員  
  
|member|說明|  
|------------|-----------------|  
|`NO_MAPPING`|原生指令的範圍不會對應到任何特殊的程式碼區域。|  
|`PROLOG`|原生指令的範圍會對應至初構。|  
|`EPILOG`|原生指令的範圍會對應到終解。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [GetILToNativeMapping 方法](icordebugcode-getiltonativemapping-method.md)
- [偵錯列舉](debugging-enumerations.md)
