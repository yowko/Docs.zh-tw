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
ms.openlocfilehash: 65de42a0b86e4b4593b7880e9dc290ce00007a40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709254"
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
 在原生程式碼中的位移位置。  
  
## <a name="remarks"></a>備註  

 呼叫以 `SetIP` 立即使目前線程的所有框架和鏈失效。 如果偵錯工具在呼叫之後需要框架資訊 `SetIP` ，則必須執行新的堆疊追蹤。  
  
 [ICorDebug](icordebug-interface.md) 會嘗試將堆疊框架保持在有效的狀態。 但是，即使框架處於有效的狀態，但在執行時間中，還是可能發生問題，例如未初始化的區域變數等等。 呼叫端負責確保執行中程式的一致性。  
  
 在64位平臺上，指令指標無法移出 `catch` 或 `finally` 封鎖。 如果 `SetIP` 呼叫以在64位平臺上進行這類移動，它會傳回指出失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
