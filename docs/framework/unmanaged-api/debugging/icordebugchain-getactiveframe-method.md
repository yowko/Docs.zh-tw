---
title: ICorDebugChain::GetActiveFrame 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: 03cb1556ee971124ed4c591f38d9f892fc7df7b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192148"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame 方法
取得鏈上的現用（也就是最新的）框架。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppFrame`  
 脫銷ICorDebugFrame 物件位址的指標，表示鏈上的現用（也就是最新的）框架。  
  
## <a name="remarks"></a>備註  
 如果沒有可用的受控堆疊框架，`ppFrame` 會設定為 null。  
  
 如果作用中的框架無法使用，呼叫將會成功，而且 `ppFrame` 將會是 null。 由於 CHAIN_ENTER_UNMANAGED，以及因 CHAIN_CLASS_INIT 而起始的部分鏈，作用中的框架將無法供使用。 請參閱 CorDebugChainReason 列舉。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
