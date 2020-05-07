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
ms.openlocfilehash: ba9a4e32216fd6fad285397bfc48fbc54f602b88
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894654"
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
 脫銷ICorDebugChain 物件位址的指標，表示呼叫的鏈。 如果這個鏈目前正在執行（也就是，如果此鏈未等候被呼叫的鏈傳回）， `ppChain`則會是 null。  
  
## <a name="remarks"></a>備註  
 這個鏈會在繼續執行之前，等待被呼叫的鏈返回。 在跨執行緒封送處理呼叫的情況下，被呼叫的鏈可能會在另一個執行緒上。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
