---
title: "ICorDebugChain::GetCallee 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b584929d99e641e361de916c402a0d5723e53c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee 方法
取得由這個鏈結所呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppChain`  
 [out]ICorDebugChain 物件，表示呼叫的鏈結的位址指標。 如果這個鏈結目前執行中 （也就是說，如果這個鏈結沒有在等待傳回呼叫的鏈結） 以及`ppChain`將會是 null。  
  
## <a name="remarks"></a>備註  
 這個鏈結將會等到前它會繼續執行，傳回呼叫的鏈結。 呼叫的鏈結可能會在跨執行緒封送處理呼叫的情況下的另一個執行緒上。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
