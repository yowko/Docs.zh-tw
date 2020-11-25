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
ms.openlocfilehash: fdc3d96fd5ad9a6ff59b863cd3f0450283ea0146
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721370"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP 方法

將指令指標設定為 Microsoft 中繼語言 (MSIL) 程式碼中指定的位移位置。  
  
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

 呼叫以 `SetIP` 立即使目前線程的所有框架和鏈失效。 如果偵錯工具在呼叫之後需要框架資訊 `SetIP` ，則必須執行新的堆疊追蹤。  
  
 [ICorDebug](icordebug-interface.md) 會嘗試將堆疊框架保持在有效的狀態。 但是，即使框架處於有效的狀態，仍可能會有一些問題，例如未初始化的區域變數。 呼叫端負責確保執行中程式的一致性。  
  
 在64位平臺上，指令指標無法移出 `catch` 或 `finally` 封鎖。 如果 `SetIP` 呼叫以在64位平臺上進行這類移動，它會傳回指出失敗的 HRESULT。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
