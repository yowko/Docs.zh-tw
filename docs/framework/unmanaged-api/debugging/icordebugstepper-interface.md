---
title: ICorDebugStepper Interface1
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 266e8c664ac7c5efa1b199efc522f0b890e38e3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepper-interface1"></a>ICorDebugStepper Interface1
表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Deactivate 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|造成這個`ICorDebugStepper`取消它所收到的最後一個步驟命令。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|取得值，指出是否此`ICorDebugStepper`目前正在執行的步驟。|  
|[SetInterceptMask 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|設定 CorDebugIntercept 值，指定類型，也就逐步執行程式碼。|  
|[SetRangeIL 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|設定值，指出是否要呼叫[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)傳遞引數的值相對於原生程式碼或正在透過逐步執行方法的 Microsoft intermediate language (MSIL) 程式碼。|  
|[SetUnmappedStopMask 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|設定 CorDebugUnmappedStop 值，指定執行將會暫止的未對應程式碼的類型。|  
|[Step 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|造成這個`ICorDebugStepper`單一步驟其包含的執行緒，以及 （選擇性） 若要繼續逐步執行緒內呼叫的函式。|  
|[StepOut 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|造成這個`ICorDebugStepper`逐步執行其包含的執行緒，以及完成時，目前的框架將控制權傳回給呼叫的框架。|  
|[StepRange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|造成這個`ICorDebugStepper`單一步驟透過其包含的執行緒，並傳回當到達指定範圍的最後一個以外的程式碼。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugStepper`介面有下列用途：  
  
-   它會充當逐步執行 命令的發出和完成的命令之間的識別項。  
  
-   它提供可執行的封裝所有的逐步執行的中央介面。  
  
-   它提供方法來提前取消逐步執行的作業。  
  
 可以有一個以上的 stepper，每個執行緒。 比方說，可能會不進入函式時叫用中斷點，使用者可能想要開始新逐步執行的作業，該函式內。 這是由偵錯工具，以決定如何處理這種情況。 偵錯工具可能想要取消原始逐步執行的作業或巢狀處理這兩項操作。 `ICorDebugStepper`介面支援這兩種選項。  
  
 如果 common language runtime (CLR) 會跨執行緒的封送處理呼叫，可能會在執行緒之間移轉 stepper。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
