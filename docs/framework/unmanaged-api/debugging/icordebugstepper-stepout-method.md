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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987424"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut 方法
會導致此 ICorDebugStepper 單一步驟透過其包含的執行緒，並完成目前的框架將控制權傳回給呼叫畫面格時。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>備註  
 A`StepOut`作業才會完成之後從目前的框架正常傳回至呼叫端的框架。  
  
 如果`StepOut`時，會呼叫 unmanaged 程式碼，在呼叫它之 managed 程式碼會傳回目前的框架時，會完成的步驟。  
  
 在.NET Framework 2.0 版中，請勿使用`StepOut`具有 STOP_UNMANAGED 旗標集因為它將會失敗。 (使用[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)將逐步執行的旗標設定。)Interop 偵錯工具必須跳離函式原生程式碼本身。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
