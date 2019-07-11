---
title: ICorDebugStepper::StepRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ace501bf5de741ea110fe4d3bb4bc44843bf8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760532"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange 方法
會導致此 ICorDebugStepper 單一步驟透過其包含的執行緒，並傳回在到達指定範圍的最後一個以外的程式碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>參數  
 `bStepIn`  
 [in]若要設定`true`逐步執行至呼叫執行緒內的函式。 若要設定`false`進入函式。  
  
 `ranges`  
 [in]每一個都會指定範圍之 COR_DEBUG_STEP_RANGE 結構陣列。  
  
 `cRangeCount`  
 [in] `ranges` 陣列的大小。  
  
## <a name="remarks"></a>備註  
 `StepRange`方法的運作方式類似[icordebugstepper:: Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)方法，不同之處在於未指定的範圍之外的程式碼直到完成為止。  
  
 這可以是比一次一個指令碼逐步偵錯更有效率。 範圍會指定為從步進框架的開頭的位移組的清單。  
  
 範圍是相對於方法的 Microsoft intermediate language (MSIL) 程式碼。 呼叫[icordebugstepper:: Setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)與`false`進行相對於方法的原生程式碼範圍。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
