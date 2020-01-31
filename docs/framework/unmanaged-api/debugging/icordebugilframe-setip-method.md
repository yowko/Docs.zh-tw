---
title: ICorDebugILFrame::SetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 466fe421f4ff3f8983159ccb38503b75551c87bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788549"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP 方法
在 Microsoft 中繼語言（MSIL）程式碼中，將指令指標設定為指定的位移位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `nOffset`  
 MSIL 程式碼中的位移位置。  
  
## <a name="remarks"></a>備註  
 `SetIP` 的呼叫會立即使目前線程的所有框架和鏈失效。 如果偵錯工具在呼叫 `SetIP`之後需要框架資訊，則必須執行新的堆疊追蹤。  
  
 [ICorDebug](icordebug-interface.md)會嘗試將堆疊框架保持在有效的狀態。 不過，即使框架處於有效的狀態，仍然可能會有一些問題，例如未初始化的區域變數。 呼叫端負責確保正在執行之程式的一致性。  
  
 在64位平臺上，無法將指令指標移出 `catch` 或 `finally` 區塊。 如果呼叫 `SetIP` 以在64位平臺上進行這類移動，則會傳回表示失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
