---
title: ICorDebugChain::GetStackRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetStackRange
helpviewer_keywords:
- ICorDebugChain::GetStackRange method [.NET Framework debugging]
- GetStackRange method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 554284e7-3f6c-4d40-8da5-1c9317fbd484
topic_type:
- apiref
ms.openlocfilehash: d9430c5a1f37a0507b383ea5437f7d7fed706c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123856"
---
# <a name="icordebugchaingetstackrange-method"></a>ICorDebugChain::GetStackRange 方法
取得此鏈之堆疊區段的位址範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>參數  
 `pStart`  
 脫銷`CORDB_ADDRESS` 值的指標，這是堆疊區段的起始位址。  
  
 `pEnd`  
 脫銷指向堆疊區段結尾位址 `CORDB_ADDRESS` 值的指標。  
  
## <a name="remarks"></a>備註  
 只有在比較堆疊框架位置時，數值範圍才有意義。 您無法針對實際儲存在堆疊上的內容進行任何假設。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
