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
ms.openlocfilehash: d9698afa2723a5d772ecf5a055f09c5ee3bc13f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727649"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange 方法

讓這個 ICorDebugStepper 在其包含的執行緒上執行一次，並在到達指定範圍的最後一個程式碼時傳回。  
  
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
 在將設定為，逐步執行在 `true` 執行緒中呼叫的函式。 設定為 `false` 以不進入函數。  
  
 `ranges`  
 在COR_DEBUG_STEP_RANGE 結構的陣列，其中每個結構都指定一個範圍。  
  
 `cRangeCount`  
 [in] `ranges` 陣列的大小。  
  
## <a name="remarks"></a>備註  

 `StepRange`方法的運作方式與[ICorDebugStepper：： Step](icordebugstepper-step-method.md)方法相同，不同之處在于它不會完成，直到到達指定範圍之外的程式碼為止。  
  
 這會比一次逐步執行一個指令更有效率。 範圍會指定為從分檔器框架開頭算起的位移組清單。  
  
 範圍是指方法的 Microsoft 中繼語言 (MSIL) 程式碼的相對路徑。 使用呼叫 [ICorDebugStepper：： SetRangeIL](icordebugstepper-setrangeil-method.md) ， `false` 使範圍相對於方法的機器碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
