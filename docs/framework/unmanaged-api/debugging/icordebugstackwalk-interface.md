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
ms.openlocfilehash: e33e9be112a6a10f89b88005496ce2e63dff2d54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782677"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk 介面
提供用來在執行緒堆疊上取得 Managed 方法或框架的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|傳回目前的框架的內容`ICorDebugStackWalk`物件。|  
|[SetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|設定`ICorDebugStackWalk`有效的內容執行緒物件的目前內容。|  
|[Next 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|移動`ICorDebugStackWalk`下一個畫面格的物件。|  
|[GetFrame 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|取得目前的框架中`ICorDebugStackWalk`物件。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
