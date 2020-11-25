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
ms.openlocfilehash: a28da34cd3080826f346b8957aa6ba38258b924f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730119"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee 方法

取得此鏈所呼叫的鏈。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppChain`  
 擴展ICorDebugChain 物件位址的指標，該物件表示呼叫的鏈。 如果此鏈目前正在執行 (也就是，如果此鏈未等候被呼叫的鏈傳回) ， `ppChain` 將會是 null。  
  
## <a name="remarks"></a>備註  

 在繼續執行之前，此鏈會等候被呼叫的鏈返回。 在跨執行緒封送呼叫的情況下，呼叫的鏈可能會在另一個執行緒上。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
