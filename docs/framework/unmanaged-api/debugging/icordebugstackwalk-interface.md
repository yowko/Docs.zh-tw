---
title: ICorDebugStackWalk 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06ce2da435df9458ca59d76fa426becbede2e619
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959680"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk 介面
提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|傳回`ICorDebugStackWalk`物件中目前框架的內容。|  
|[SetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|`ICorDebugStackWalk`將物件的目前內容設定為執行緒的有效內容。|  
|[Next 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|`ICorDebugStackWalk`將物件移到下一個框架。|  
|[GetFrame 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|取得`ICorDebugStackWalk`物件中的目前框架。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
