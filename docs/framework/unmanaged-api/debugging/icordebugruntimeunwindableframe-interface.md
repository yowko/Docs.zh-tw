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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e2edc64cd9067ed89ae0e309c6a5630319ce835
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame 介面
提供 Unmanaged 方法的支援，這些方法需要通用語言執行平台 (CLR) 才能回溯框架。  
  
## <a name="remarks"></a>備註  
 `ICorDebugRuntimeUnwindableFrame` 是特殊的版的 ICorDebugFrame 介面。 它會使用 unmanaged 需要回溯上目前的堆疊框架執行階段的方法。 現有的回溯慣例沒有作用，因為它們不會使用 JIT 編譯程式碼。 當偵錯工具看到無法還原的畫面格時，應該使用[icordebugstackwalk:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)回溯，但是它的方法應該會執行本身的檢查。 當偵錯工具收到`ICorDebugRuntimeUnwindableFrame`，它可以呼叫[icordebugstackwalk:: Getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)方法來擷取框架的內容。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
