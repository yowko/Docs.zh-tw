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
ms.openlocfilehash: 3ca062231fd482c1f0d888935e882513461838ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137600"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper 介面
表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Deactivate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|導致此 `ICorDebugStepper` 取消所收到的最後一個步驟命令。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|取得值，指出此 `ICorDebugStepper` 目前是否正在執行步驟。|  
|[SetInterceptMask 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|設定 CorDebugIntercept 值，指定要逐步執行的程式碼類型。|  
|[SetRangeIL 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|設定值，指出是否呼叫[ICorDebugStepper：： StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)傳遞引數值相對於要逐步執行之方法的原生程式碼或 Microsoft 中繼語言（MSIL）程式碼。|  
|[SetUnmappedStopMask 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|設定 CorDebugUnmappedStop 值，指定將暫停執行的未對應程式碼類型。|  
|[Step 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|使此 `ICorDebugStepper` 單一步驟逐步執行其包含的執行緒，並選擇性地繼續透過線上程內呼叫的函式進行單一逐步執行。|  
|[StepOut 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|使此 `ICorDebugStepper` 在其包含的執行緒上執行單一步驟，並在目前的框架將控制項傳回至呼叫的框架時完成。|  
|[StepRange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|使此 `ICorDebugStepper` 在其包含的執行緒上執行單一步驟，並在到達超出指定範圍的最後一個程式碼時傳回。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugStepper` 介面有下列用途：  
  
- 它會做為所發出的步驟命令和該命令完成之間的識別碼。  
  
- 它提供一個中央介面來封裝可執行檔所有逐步執行。  
  
- 它提供了一種方法，可讓您提前取消逐步操作。  
  
 每個執行緒可以有一個以上的分檔器。 例如，在逐步執行函式時，可能會叫用中斷點，而且使用者可能會想要在該函式內啟動新的逐步操作。 偵錯工具會決定如何處理這種情況。 偵錯工具可能會想要取消原始的逐步執行作業，或將兩個運算加以嵌套。 `ICorDebugStepper` 介面支援這兩種選擇。  
  
 如果 common language runtime （CLR）進行跨執行緒、封送處理的呼叫，則分檔器可以線上程之間進行遷移。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
