---
title: VariableLocationType 列舉
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: 1aa59ee559abff8006f0ac63a812e4315aa48154
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790302"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType 列舉
表示變數的原生位置類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`VLT_REGISTER`|變數在暫存器中。|  
|`VLT_REGISTER_RELATIVE`|變數位於暫存器相對的記憶體位置。|  
|`VLT_INVALID`|此變數不會儲存在暫存器或登錄相對的記憶體位置。|  
  
## <a name="remarks"></a>備註  
 [ICorDebugVariableHome：： GetLocationType](icordebugvariablehome-getlocationtype-method.md)方法會傳回 `VariableLocationType` 列舉的成員。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
