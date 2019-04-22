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
ms.openlocfilehash: 745917af176de47999737c87833c23df9c75ea7b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080861"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval 介面

提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|中止計算這`ICorDebugEval`物件目前正在執行。|  
|[CallFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|設定指定的函式的呼叫。 (.NET Framework 2.0 版中已淘汰; 請改用[ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)改用。)|  
|[CreateValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|取得"ICorDebugValue 」 物件的指定類型的介面指標，其初始值為零或 null。 (.NET Framework 2.0 中已淘汰; 請改用[ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)改用。)|  
|[GetResult 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|取得的介面指標`ICorDebugValue`包含評估的結果。|  
|[GetThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|取得"ICorDebugThread 」 這項評估其中正在執行或即將執行的介面指標。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|取得值，指出是否此`ICorDebugEval`物件目前正在執行。|  
|[NewArray 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|配置的指定項目類型和維度的新陣列。 (.NET Framework 2.0 中已淘汰; 請改用[ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)改用。)|  
|[NewObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|配置新的物件執行個體，並呼叫指定的建構函式方法。 (.NET Framework 2.0 中已淘汰; 請改用[ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)改用。)|  
|[NewObjectNoConstructor 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|配置新的物件執行個體，指定的類型，而不會嘗試呼叫建構函式方法。 (.NET Framework 2.0 中已淘汰; 請改用[ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)改用。)|  
|[NewString 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|會配置新的字串物件，具有指定的內容。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugEval`用來執行評估在特定執行緒的內容中建立物件。 所有物件和指定的評估中使用的類型必須都位於相同的應用程式定義域。 該應用程式定義域不需要相同的執行緒目前的應用程式定義域。 可以是巢狀的評估。  
  
 評估作業未完成之前，偵錯工具會呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)，然後接收[icordebugmanagedcallback:: Evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)回呼。 如果您需要使用 「 評估 」 功能，不允許執行其他執行緒，暫止執行緒使用其中一種[icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)或[icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)再呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)。  
  
 因為在進行評估時，正在執行使用者程式碼，都會發生任何偵錯事件，包括類別載入和中斷點。 偵錯工具將會收到一般，這些事件的回呼。 評估的狀態將會被視為屬於正常的程式狀態的檢查。 堆疊鏈結將會`CHAIN_FUNC_EVAL`鏈結 (請參閱 「 CorDebugStepReason"列舉和[icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)方法)。 完整的偵錯工具 API 會繼續正常運作。  
  
 如果發生的死結或無限迴圈的情況下，使用者程式碼可能永遠無法完成。 在此情況下，您必須呼叫[icordebugeval:: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)再繼續程式。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
