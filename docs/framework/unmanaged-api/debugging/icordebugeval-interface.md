---
title: ICorDebugEval Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77e97e31a20c392eebae1b373bb1af53f87c23e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval-interface1"></a>ICorDebugEval Interface1
提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|這個中止計算`ICorDebugEval`物件目前正在執行。|  
|[CallFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|設定指定函式的呼叫。 (.NET Framework 2.0 版中已過時; 使用[icordebugeval2:: Callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)改用。)|  
|[CreateValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|取得的介面指標 」 ICorDebugValue 」 指定型別的物件，其初始值為零或 null。 (.NET Framework 2.0 中已過時; 使用[icordebugeval2:: Createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)改用。)|  
|[GetResult 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|取得的介面指標`ICorDebugValue`包含評估的結果。|  
|[GetThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|取得"ICorDebugThread 」 這項評估其中正在執行，或是將執行的介面指標。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|取得值，指出是否此`ICorDebugEval`物件目前正在執行。|  
|[NewArray 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|配置的指定項目類型和維度的新陣列。 (.NET Framework 2.0 中已過時; 使用[icordebugeval2:: Newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)改用。)|  
|[NewObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|配置新的物件執行個體並呼叫指定的建構函式方法。 (.NET Framework 2.0 中已過時; 使用[icordebugeval2:: Newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)改用。)|  
|[NewObjectNoConstructor 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|配置新的物件執行個體指定的類型，而不會嘗試呼叫建構函式方法。 (.NET Framework 2.0 中已過時; 使用[icordebugeval2:: Newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)改用。)|  
|[NewString 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|會配置新的 string 物件具有指定的內容。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugEval`特定執行緒用來執行評估的內容中建立物件。 所有物件和指定的評估中使用的類型必須都位於相同的應用程式網域中。 應用程式定義域不需要是執行緒的相同目前的應用程式定義域。 評估可以是巢狀。  
  
 評估作業無法完成直到偵錯工具呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)，，然後接收[icordebugmanagedcallback:: Evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)回呼。 如果您需要使用不允許執行其他執行緒的評估功能，請使用暫停執行緒[icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)或[icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)之前先呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)。  
  
 因為正在進行評估時，正在執行使用者程式碼，可能發生的任何偵錯事件，包括類別載入和中斷點。 偵錯工具將接收回撥，按照一般，這些事件。 評估的狀態會被視為屬於正常的程式狀態的檢查。 堆疊鏈結將會`CHAIN_FUNC_EVAL`鏈結 (請參閱 「 CorDebugStepReason"列舉和[icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)方法)。 完整的偵錯工具應用程式開發介面會繼續正常運作。  
  
 如果發生的死結或無限迴圈的情況下，使用者程式碼可能永遠無法完成。 在這種情況下，您必須呼叫[icordebugeval:: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)之前繼續執行程式。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
    
    
    
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
