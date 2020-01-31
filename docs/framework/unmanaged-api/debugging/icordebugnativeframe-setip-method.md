---
title: ICorDebugNativeFrame::SetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: bc33768e4155a0e272d3374d4c586c79ef2ff3fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792772"
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP 方法
將指令指標設定為原生程式碼中指定的位移位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `nOffset`  
 在機器碼中的位移位置。  
  
## <a name="remarks"></a>備註  
 `SetIP` 的呼叫會立即使目前線程的所有框架和鏈失效。 如果偵錯工具在呼叫 `SetIP`之後需要框架資訊，則必須執行新的堆疊追蹤。  
  
 [ICorDebug](icordebug-interface.md)會嘗試將堆疊框架保持在有效的狀態。 不過，即使畫面格處於有效的狀態，只要執行時間關心，仍然可能會有問題，例如未初始化的區域變數等等。 呼叫端負責確保執行中程式的一致性。  
  
 在64位平臺上，無法將指令指標移出 `catch` 或 `finally` 區塊。 如果呼叫 `SetIP` 以在64位平臺上進行這類移動，則會傳回表示失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱
