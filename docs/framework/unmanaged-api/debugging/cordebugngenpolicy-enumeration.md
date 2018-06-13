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
ms.openlocfilehash: cc5a06e6b3cc1e9338d860cdb110bf7d516080be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404020"
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
|`DISABLE_LOCAL_NIC`|在[!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)]應用程式中，使用影像，從本機原生映像快取已停用。 在傳統型應用程式，這項設定沒有任何作用。|  
  
## <a name="remarks"></a>備註  
 `CorDebugNGENPolicy`項列舉供[icordebugprocess5:: Enablengenpolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)方法。 停用映像從本機原生映像快取的使用方法是確保偵錯工具載入偵錯 JIT 編譯的影像，而不是最佳化的原生映像提供一致的偵錯經驗。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
