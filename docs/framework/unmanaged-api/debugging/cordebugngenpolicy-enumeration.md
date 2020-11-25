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
ms.openlocfilehash: b64de0fa2ecbddd2decf69a4099d9897ec42a563
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696423"
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
|`DISABLE_LOCAL_NIC`|在 Windows 8. x 存放區應用程式中，會停用本機原生映射快取中的映射。 在桌面應用程式中，此設定沒有任何作用。|  
  
## <a name="remarks"></a>備註  

 `CorDebugNGENPolicy` [ICorDebugProcess5：： EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md)方法會使用列舉。 停用本機原生映射快取中的映射使用，可確保偵錯工具載入可調試的 JIT 編譯影像，而不是優化的原生映射，以提供一致的偵錯工具。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
