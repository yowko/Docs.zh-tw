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
ms.openlocfilehash: daecd216b4d7e9c23336b8956c13735549be901b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730132"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame 方法

取得使用中的 (，也就是鏈上最新的) 框架。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppFrame`  
 擴展ICorDebugFrame 物件位址的指標，該物件表示目前的使用中 (，也就是最新的) 框架。  
  
## <a name="remarks"></a>備註  

 如果沒有可用的受控堆疊框架， `ppFrame` 會設為 null。  
  
 如果使用中的框架無法使用，則呼叫會成功，而且 `ppFrame` 將會是 null。 使用中的框架將無法用於因為 CHAIN_ENTER_UNMANAGED 所起始的鏈，以及因 CHAIN_CLASS_INIT 而起始的部分鏈。 請參閱 CorDebugChainReason 列舉。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
