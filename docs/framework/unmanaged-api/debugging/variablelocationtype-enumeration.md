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
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178354"
---
# <a name="variablelocationtype-enumeration"></a>VariableLocationType 列舉
指示變數的本機位置類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`VLT_REGISTER`|變數在寄存器中。|  
|`VLT_REGISTER_RELATIVE`|變數位於寄存器相對記憶體位置。|  
|`VLT_INVALID`|變數不存儲在寄存器或寄存器相對記憶體位置。|  
  
## <a name="remarks"></a>備註  
 枚舉的成員`VariableLocationType`由[ICorDebugvariableHome：：獲取定位類型](icordebugvariablehome-getlocationtype-method.md)方法返回。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
