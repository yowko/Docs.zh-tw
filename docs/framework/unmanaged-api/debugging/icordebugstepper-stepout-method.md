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
ms.openlocfilehash: 1396e7a8ca61734a9363a9c852502290675249d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727662"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut 方法

讓這個 ICorDebugStepper 在其包含的執行緒上執行一次，並在目前的框架將控制權傳回給呼叫的框架時完成。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>備註  

 `StepOut`從目前的框架傳回至呼叫框架之後，作業將會完成。  
  
 如果 `StepOut` 在非受控程式碼中呼叫，當目前的框架返回呼叫它的 managed 程式碼時，就會完成此步驟。  
  
 在 .NET Framework 2.0 版中，請勿使用 `StepOut` with STOP_UNMANAGED 旗標設定，因為它會失敗。  (使用 [ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) 來設定逐步執行的旗標。 ) Interop 偵錯工具必須跳出機器碼本身。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
