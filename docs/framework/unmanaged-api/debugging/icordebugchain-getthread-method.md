---
title: ICorDebugChain::GetThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05002ecdb903a1adfeea88930083ba472164324
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745632"
---
# <a name="icordebugchaingetthread-method"></a>ICorDebugChain::GetThread 方法
取得實體的執行緒，此呼叫鏈結的一部分。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppThread`  
 [out]指向 ICorDebugThread 物件，表示實體執行緒的這個呼叫鏈結是的一部分。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
