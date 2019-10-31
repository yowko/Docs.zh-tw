---
title: ICorDebugRuntimeUnwindableFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: 2902744b6af3c7b2bd4def73b04807ce3333a8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131894"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame 介面
提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。  
  
## <a name="remarks"></a>備註  
 `ICorDebugRuntimeUnwindableFrame` 是 ICorDebugFrame 介面的特殊化版本。 這是由需要執行時間在目前堆疊上回溯框架的非受控方法所使用。 現有的回溯慣例無法正常執行，因為它們不會使用 JIT 編譯的程式碼。 當偵錯工具看到 unwindable 框架時，應該使用[ICorDebugStackWalk：： Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)方法來回溯它，但它應該執行檢查本身。 當偵錯工具收到 `ICorDebugRuntimeUnwindableFrame`時，它可以呼叫[ICorDebugStackWalk：： GetCoNtext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)方法來取出框架的內容。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
