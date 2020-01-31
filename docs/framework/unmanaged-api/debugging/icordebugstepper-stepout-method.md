---
title: ICorDebugStepper::StepOut 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 08cf2d0bb09080296fc1fcc69b5817f4d6118765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791719"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut 方法
使此 ICorDebugStepper 逐步執行其包含的執行緒，並在目前的框架將控制項傳回至呼叫的框架時完成。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>備註  
 `StepOut` 作業會在從目前的框架正常傳回至呼叫框架之後完成。  
  
 如果在非受控碼中呼叫 `StepOut`，當目前的框架回到呼叫它的 managed 程式碼時，步驟就會完成。  
  
 在 .NET Framework 版本2.0 中，請勿使用已設定 STOP_UNMANAGED 旗標的 `StepOut`，因為它將會失敗。 （使用[ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)來設定逐步執行的旗標）。Interop 偵錯工具必須以機器碼本身的模式執行。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
