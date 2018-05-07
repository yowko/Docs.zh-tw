---
title: CorDebugStateChange 列舉
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 841108457293e3377ee87f9c7d7c6898340e51b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange 列舉
描述依據處理序變更而必須捨棄的快取資料量。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`PROCESS_RUNNING`|處理序透過向前執行已達到新的記憶體狀態。|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|指定的處理序記憶體可能與先前的記憶體不同。|  
  
## <a name="remarks"></a>備註  
 成員`CorDebugStateChange`列舉型別提供做為引數時偵錯工具呼叫[ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)方法  
  
> [!NOTE]
>  這個列舉僅適用於 .NET 原生偵錯案例。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
