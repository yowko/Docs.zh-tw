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
ms.openlocfilehash: 5a07550d44857526e8ab4ded9f1827ef12e3bba4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192142"
---
# <a name="icordebugchaingetcaller-method"></a>ICorDebugChain::GetCaller 方法
取得呼叫這個鏈的鏈。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppChain`  
 脫銷代表呼叫鏈之 ICorDebugChain 物件位址的指標。  
  
 如果這個鏈是自發呼叫的（例如，如果這個鏈或偵錯工具已初始化呼叫堆疊），`ppChain` 將會是 null。  
  
## <a name="remarks"></a>備註  
 如果呼叫是線上程之間封送處理，則呼叫鏈可能會在不同的執行緒上。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
