---
title: ICorDebugStepper 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: 8b5bbb65034e5b715532397c9ecc650da9aee912
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718289"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper 介面

表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Deactivate 方法](icordebugstepper-deactivate-method.md)|造成此問題 `ICorDebugStepper` 取消其收到的最後一個步驟命令。|  
|[IsActive 方法](icordebugstepper-isactive-method.md)|取得值，這個值表示目前是否正在 `ICorDebugStepper` 執行步驟。|  
|[SetInterceptMask 方法](icordebugstepper-setinterceptmask-method.md)|設定 CorDebugIntercept 值，指定逐步執行的程式碼類型。|  
|[SetRangeIL 方法](icordebugstepper-setrangeil-method.md)|設定值，這個值會指出呼叫 [ICorDebugStepper：： StepRange](icordebugstepper-steprange-method.md) 是否會傳遞引數值（相對於原生程式碼）或 Microsoft 中繼語言 (MSIL) 正在逐步執行之方法的程式碼。|  
|[SetUnmappedStopMask 方法](icordebugstepper-setunmappedstopmask-method.md)|設定 CorDebugUnmappedStop 值，指定要在其中停止執行的未對應程式碼類型。|  
|[Step 方法](icordebugstepper-step-method.md)|會讓此動作 `ICorDebugStepper` 逐步完成其包含執行緒，並選擇性地透過線上程中呼叫的函式來繼續進行單一逐步執行。|  
|[StepOut 方法](icordebugstepper-stepout-method.md)|使 `ICorDebugStepper` 其在包含的執行緒中執行單一步驟，並在目前的框架將控制權傳回給呼叫的框架時完成。|  
|[StepRange 方法](icordebugstepper-steprange-method.md)|使 `ICorDebugStepper` 其在包含的執行緒上進行單一步驟，並在到達指定範圍的最後一個程式碼時傳回。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugStepper`介面可作為下列用途：  
  
- 它會做為發出的步驟命令和該命令完成之間的識別碼。  
  
- 它會提供中央介面，以封裝可執行檔所有逐步執行。  
  
- 它提供了一種提前取消逐步執行作業的方法。  
  
 每個執行緒可以有一個以上的分檔器。 例如，在執行函式時可能會叫用中斷點，而使用者可能會想要在該函式內啟動新的逐步執行作業。 偵錯工具會決定如何處理這種情況。 偵錯工具可能會想要取消原始的逐步執行作業或嵌套兩個作業。 `ICorDebugStepper`介面同時支援這兩種選擇。  
  
 如果 common language runtime (CLR) 建立跨執行緒、封送處理的呼叫，則可以線上程之間遷移分檔器。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
