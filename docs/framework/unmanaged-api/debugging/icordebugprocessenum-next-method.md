---
title: ICorDebugProcessEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: 6aee88452819a4aabe2a29971ce86079ef7f0008
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732498"
---
# <a name="icordebugprocessenumnext-method"></a>ICorDebugProcessEnum::Next 方法

從目前位置開始，取得列舉中指定的 ICorDebugProcess 實例數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  

 `celt`  
 在 `ICorDebugProcess` 要取出的實例數目。  
  
 `processes`  
 擴展指標的陣列，每個指標 `ICorDebugProcess` 都會指向代表進程的物件。  
  
 `pceltFetched`  
 擴展實際傳回之實例數目的指標 `ICorDebugProcess` 。 如果是1，則這個值可能是 null `celt` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
