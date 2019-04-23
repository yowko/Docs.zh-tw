---
title: CorDebugNGenPolicy 列舉
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca922d8b582c0608073d4fd0ba986167ae470e34
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109664"
---
# <a name="cordebugngenpolicy-enumeration"></a>CorDebugNGenPolicy 列舉
提供用來判定偵錯工具是否從原生影像快取載入原生 (NGen) 影像的值。  
  
## <a name="syntax"></a>語法  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a>成員  
  
|成員名稱|描述|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|在 [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)]已停用應用程式，從本機原生映像快取的影像之使用。 在桌面應用程式中，這項設定沒有任何作用。|  
  
## <a name="remarks"></a>備註  
 `CorDebugNGENPolicy`列舉由[ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)方法。 停用的本機原生映像快取中的映像使用一致的偵錯經驗可確保提供偵錯工具會載入可偵錯的 JIT 編譯映像，而不是最佳化的原生映像。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
