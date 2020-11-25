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
ms.openlocfilehash: 50fad8b38a6b33d0ddbb2f0f20676296c3d66737
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698724"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask 方法

設定值，這個值會指定要在其中停止執行的未對應程式碼類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>參數  

 `mask`  
 在CorDebugUnmappedStop 列舉的值，這個值會指定偵錯工具將在其中停止執行的未對應程式碼類型。  
  
 預設值為 STOP_OTHER_UNMAPPED。 值 STOP_UNMANAGED 僅適用于 interop 的偵錯工具。  
  
## <a name="remarks"></a>備註  

 當偵錯工具找不到與 Microsoft 中繼語言 (MSIL) 對應的即時 (JIT) 編譯時，如果已設定未對應程式碼類型的旗標，則會中止執行;否則，會以透明的方式繼續執行。  
  
 如果偵錯工具未使用分檔器來輸入方法，則不一定不會跳過未對應的程式碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
