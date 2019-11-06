---
title: ICorDebugChain::GetCallee 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 5d28af09faae84b0482d438ae33f593f250490c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196331"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee 方法
取得這個鏈所呼叫的鏈。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppChain`  
 脫銷ICorDebugChain 物件位址的指標，表示呼叫的鏈。 如果目前正在執行此鏈（也就是，如果此鏈未等候被呼叫的鏈傳回），`ppChain` 將會是 null。  
  
## <a name="remarks"></a>備註  
 這個鏈會在繼續執行之前，等待被呼叫的鏈返回。 在跨執行緒封送處理呼叫的情況下，被呼叫的鏈可能會在另一個執行緒上。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
