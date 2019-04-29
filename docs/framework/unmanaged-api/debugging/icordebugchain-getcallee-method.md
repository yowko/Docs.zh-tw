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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed5a7657affde335acf79952d77bbdb7ac42c7a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645290"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee 方法
取得這個鏈結所呼叫函式鏈結。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppChain`  
 [out]ICorDebugChain 物件，表示呼叫的鏈結的位址指標。 如果這個鏈結目前執行中 （亦即，如果這個鏈結不會等候到傳回的呼叫鏈結） 以及`ppChain`將會是 null。  
  
## <a name="remarks"></a>備註  
 這個鏈結會等待呼叫的鏈結，以便繼續執行之前傳回。 呼叫的鏈結可能會在跨執行緒封送處理呼叫的情況下的另一個執行緒上。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
