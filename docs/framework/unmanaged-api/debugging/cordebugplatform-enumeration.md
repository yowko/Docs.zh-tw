---
title: CorDebugPlatform 列舉
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
ms.openlocfilehash: fdb03b9244d3cb351735f5f2214248a08a399188
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795738"
---
# <a name="cordebugplatform-enumeration"></a>CorDebugPlatform 列舉
提供[ICorDebugDataTarget：： GetPlatform](icordebugdatatarget-getplatform-method.md)方法所使用的目標平臺值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>成員  
  
|member|說明|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|目標平台是在 Intel x86 硬體上執行的 Windows。|  
|CORDB_PLATFORM_WINDOWS_AMD64|目標平台是在 AMD64 或 Intel EM64T 硬體上執行的 64 位元 Windows。|  
|CORDB_PLATFORM_WINDOWS_IA64|目標平台是在 Intel IA-64 硬體上執行的 32 位元 Windows。|  
|CORDB_PLATFORM_MAC_PPC|目標平臺是在 PowerPC 硬體上執行的 Macintosh 作業系統。|  
|CORDB_PLATFORM_MAC_X86|目標平臺是在 Intel x86 硬體上執行的 Macintosh 作業系統。|  
|CORDB_PLATFORM_WINDOWS_ARM|目標平臺是在 Windows ARM 硬體上執行的 Macintosh 作業系統。|  
|CORDB_PLATFORM_MAC_AMD64|目標平臺是在 AMD64 硬體上執行的 Macintosh 作業系統。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 .NET Framework 4.5.2 及更新版本中有提供 `CORDB_PLATFORM_WINDOWS_ARM` 及 `CORDB_PLATFORM_MAC_AMD64` 成員。  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
