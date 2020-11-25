---
title: ICorDebugChain::GetCaller 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
ms.openlocfilehash: 0f616b3bae48a972c0fc8935c35add7d844a7364
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730106"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller 方法

取得呼叫此鏈的鏈。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppChain`  
 擴展ICorDebugChain 物件位址的指標，代表呼叫鏈。  
  
 如果這個鏈是以自發方式呼叫 (就像是此鏈或偵錯工具初始化呼叫堆疊) 的情況一樣， `ppChain` 將會是 null。  
  
## <a name="remarks"></a>備註  

 如果呼叫是跨執行緒封送處理，則呼叫鏈可能會在不同的執行緒上。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
