---
title: ICorDebugEval 介面
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd29067f819ba69305f7ae8620729cd443915a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931940"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval 介面

提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|中止此`ICorDebugEval`物件目前正在執行的計算。|  
|[CallFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|設定對指定函數的呼叫。 (在 .NET Framework 版本2.0 中已過時; 請改用[ICorDebugEval2:: CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) 。)|  
|[CreateValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|取得指定類型之 "ICorDebugValue" 物件的介面指標, 其初始值為零或 null。 (在 .NET Framework 2.0 中已過時; 請改用[ICorDebugEval2:: CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) )。|  
|[GetResult 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|取得的介面指標`ICorDebugValue` , 其中包含評估的結果。|  
|[GetThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|取得此評估正在執行或將執行之 "ICorDebugThread" 的介面指標。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|取得值, 指出這個`ICorDebugEval`物件目前是否正在執行。|  
|[NewArray 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|配置指定之元素類型和維度的新陣列。 (在 .NET Framework 2.0 中已過時; 請改用[ICorDebugEval2:: NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) )。|  
|[NewObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|配置新的物件實例, 並呼叫指定的函式方法。 (在 .NET Framework 2.0 中已過時; 請改用[ICorDebugEval2:: NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) )。|  
|[NewObjectNoConstructor 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|配置指定類型的新物件實例, 而不會嘗試呼叫函式方法。 (在 .NET Framework 2.0 中已過時; 請改用[ICorDebugEval2:: NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) )。|  
|[NewString 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|使用指定的內容, 配置新的字串物件。|  
  
## <a name="remarks"></a>備註  
 在用來執行評估的特定執行緒內容中, 會建立物件。`ICorDebugEval` 指定評估中使用的所有物件和類型都必須位於相同的應用程式域中。 該應用程式域不需要與執行緒目前的應用程式域相同。 可以嵌套評估。  
  
 在偵錯工具呼叫[ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)之後, 評估的作業才會完成, 然後接收[ICorDebugManagedCallback:: EvalComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)回呼。 如果您需要使用評估功能而不允許其他執行緒執行, 請使用[ICorDebugController:: SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)或[ICorDebugController:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)來暫停執行緒, 然後再呼叫[ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)。  
  
 因為使用者程式碼正在進行評估, 所以可能會發生任何 debug 事件, 包括類別載入和中斷點。 偵錯工具會如往常般接收這些事件的回呼。 評估的狀態將會視為一般程式狀態檢查的一部分。 堆疊鏈會是一種`CHAIN_FUNC_EVAL`鏈 (請參閱 "CorDebugStepReason" 列舉和[ICorDebugChain:: GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)方法)。 完整的偵錯工具 API 會繼續正常運作。  
  
 如果發生鎖死或無限迴圈的情況, 使用者程式碼可能永遠不會完成。 在這種情況下, 您必須先呼叫[ICorDebugEval:: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) , 才能繼續執行程式。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
