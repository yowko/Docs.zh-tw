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
ms.openlocfilehash: 5d8fd79b242f2b88b82c5c3d78dfe45d80f1194f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729781"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval 介面

提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](icordebugeval-abort-method.md)|中止此 `ICorDebugEval` 物件目前正在執行的計算。|  
|[CallFunction 方法](icordebugeval-callfunction-method.md)|設定指定之函數的呼叫。  (在 .NET Framework 2.0 版中淘汰;請改用 [ICorDebugEval2：： CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) 。 ) |  
|[CreateValue 方法](icordebugeval-createvalue-method.md)|取得指定類型之 "ICorDebugValue" 物件的介面指標，其初始值為零或 null。  (在 .NET Framework 2.0 中淘汰;請改用 [ICorDebugEval2：： CreateValueForType](icordebugeval2-createvaluefortype-method.md) 。 ) |  
|[GetResult 方法](icordebugeval-getresult-method.md)|取得的介面指標 `ICorDebugValue` ，其中包含評估的結果。|  
|[GetThread 方法](icordebugeval-getthread-method.md)|取得「ICorDebugThread」的介面指標，此評估正在執行或將會執行。|  
|[IsActive 方法](icordebugeval-isactive-method.md)|取得值，這個值會指出這個 `ICorDebugEval` 物件目前是否正在執行。|  
|[NewArray 方法](icordebugeval-newarray-method.md)|配置指定元素類型和維度的新陣列。  (在 .NET Framework 2.0 中淘汰;請改用 [ICorDebugEval2：： NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) 。 ) |  
|[NewObject 方法](icordebugeval-newobject-method.md)|配置新的物件實例，並呼叫指定的函式方法。  (在 .NET Framework 2.0 中淘汰;請改用 [ICorDebugEval2：： NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) 。 ) |  
|[NewObjectNoConstructor 方法](icordebugeval-newobjectnoconstructor-method.md)|配置指定類型的新物件實例，而不嘗試呼叫函式方法。  (在 .NET Framework 2.0 中淘汰;請改用 [ICorDebugEval2：： NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) 。 ) |  
|[NewString 方法](icordebugeval-newstring-method.md)|使用指定的內容配置新的字串物件。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugEval`物件是在用來執行評估的特定執行緒內容中建立的。 指定評估中使用的所有物件和類型都必須位於相同的應用程式域中。 該應用程式域不需要與執行緒目前的應用程式域相同。 評估可以進行嵌套。  
  
 除非偵錯工具呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md)，然後收到 [ICorDebugManagedCallback：： EvalComplete](icordebugmanagedcallback-evalcomplete-method.md) 回呼，否則評估的作業不會完成。 如果您需要使用評估功能，而不允許其他執行緒執行，請在呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)之前，使用[ICorDebugController：： SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md)或[ICorDebugController：： Stop](icordebugcontroller-stop-method.md)來暫停執行緒。  
  
 因為正在進行評估時，使用者程式碼正在執行，所以可能會發生任何 debug 事件，包括類別載入和中斷點。 偵錯工具會如往常般接收這些事件的回呼。 評估的狀態將會顯示為檢查正常程式狀態的一部分。 堆疊鏈將會是 `CHAIN_FUNC_EVAL` 鏈 (請參閱 "CorDebugStepReason" 列舉和 [ICorDebugChain：： GetReason](icordebugchain-getreason-method.md) 方法) 。 完整的偵錯工具 API 將繼續正常運作。  
  
 如果發生鎖死或無限迴圈的狀況，使用者程式碼可能永遠不會完成。 在這種情況下，您必須先呼叫 [ICorDebugEval：： Abort](icordebugeval-abort-method.md) ，然後再繼續此程式。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
