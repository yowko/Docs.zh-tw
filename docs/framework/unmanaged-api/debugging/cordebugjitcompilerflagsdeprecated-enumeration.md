---
title: CorDebugJITCompilerFlagsDeprecated 列舉
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: 7b8a726cffcc00d7371675192a209b2d8e9db94d
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795777"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a>CorDebugJITCompilerFlagsDeprecated 列舉
這個列舉已過時。 請改用`CORDEBUG_JIT_DEFAULT` [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md)列舉的成員。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a>成員  
  
|member|說明|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|請改用 `CORDEBUG_JIT_DEFAULT`。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
