---
title: ICorDebugChainEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 0f42020821ec71d1e59ae8097f22ee530e16a576
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706173"
---
# <a name="icordebugchainenumnext-method"></a>ICorDebugChainEnum::Next 方法

從目前位置開始，取得列舉中指定的 ICorDebugChain 實例數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  

 `celt`  
 在 `ICorDebugChain` 要取出的實例數目。  
  
 `chains`  
 擴展指標的陣列，每個指標 `ICorDebugChain` 都會指向代表一個鏈的物件。  
  
 `pceltFetched`  
 擴展實際傳回之實例數目的指標 `ICorDebugChain` 。 如果是1，則這個值可能是 null `celt` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
