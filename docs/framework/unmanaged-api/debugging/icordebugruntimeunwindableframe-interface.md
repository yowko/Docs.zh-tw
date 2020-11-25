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
ms.openlocfilehash: 6619b8888588341f23a93b83865cd2e75cc9b3db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712010"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame 介面

提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。  
  
## <a name="remarks"></a>備註  

 `ICorDebugRuntimeUnwindableFrame` 是 ICorDebugFrame 介面的特製化版本。 它是由要求執行時間在目前堆疊上回溯框架的非受控方法所使用。 現有的回溯慣例無法運作，因為它們不會使用 JIT 編譯的程式碼。 當偵錯工具看到 unwindable 框架時，它應該使用 [ICorDebugStackWalk：： Next](icordebugstackwalk-next-method.md) 方法來將它回溯，但它應該會執行檢查。 當偵錯工具收到時 `ICorDebugRuntimeUnwindableFrame` ，它可以呼叫 [ICorDebugStackWalk：： GetCoNtext](icordebugstackwalk-getcontext-method.md) 方法來取出框架的內容。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
