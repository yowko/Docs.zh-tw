---
title: ICorDebugStepper::SetUnmappedStopMask 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc4e51ec60c7526f36bbe4909bec91a527e0862c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask 方法
設定值，指定執行將會暫止的未對應程式碼的類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a>參數  
 `mask`  
 [in]指定類型的未對應的程式碼中偵錯工具將會暫止執行 CorDebugUnmappedStop 列舉值。  
  
 預設值是 STOP_OTHER_UNMAPPED。 值 STOP_UNMANAGED 只適用於 interop 偵錯。  
  
## <a name="remarks"></a>備註  
 當偵錯工具找到在 just-in-time (JIT) 編譯成 Microsoft intermediate language (MSIL) 沒有對應的對應時，它會中止執行如果已設定旗標，指定該類型的未對應的程式碼;否則，以透明的方式逐步執行會繼續。  
  
 如果偵錯工具不會使用 stepper 輸入方法，然後它不一定不進入未對應的程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
