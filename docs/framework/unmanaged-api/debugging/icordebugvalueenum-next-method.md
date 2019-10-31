---
title: ICorDebugValueEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: 09394acb07b8595f99d9ecc873eb0985cdd79316
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134589"
---
# <a name="icordebugvalueenumnext-method"></a>ICorDebugValueEnum::Next 方法
從列舉中取得指定數目的 "ICorDebugValue" 實例，從目前位置開始。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
 在要抓取 `ICorDebugValue` 實例的數目。  
  
 `values`  
 脫銷指標陣列，其中每一個都會指向 `ICorDebugValue` 物件。  
  
 `pceltFetched`  
 脫銷實際傳回的 `ICorDebugValue` 實例數目的指標。 如果 `celt` 是一個，這個值可能會是 null。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱
