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
ms.openlocfilehash: ff393b119c349e34898b781c3185cc82f2dba11f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137557"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask 方法
設定值，指定執行將暫停的未對應程式碼類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>參數  
 `mask`  
 在CorDebugUnmappedStop 列舉的值，指定偵錯工具將在其中停止執行的未對應程式碼類型。  
  
 預設值為 STOP_OTHER_UNMAPPED。 STOP_UNMANAGED 值只適用于 interop 調試。  
  
## <a name="remarks"></a>備註  
 當偵錯工具發現沒有對應到 Microsoft 中繼語言（MSIL）的即時（JIT）編譯時，如果指定該類型之未對應程式碼的旗標已設定，就會停止執行。否則，逐步執行會以透明方式繼續進行。  
  
 如果偵錯工具未使用分檔器來輸入方法，則不一定會跳過未對應的程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
