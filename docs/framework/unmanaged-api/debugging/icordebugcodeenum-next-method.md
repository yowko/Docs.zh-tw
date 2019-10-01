---
title: ICorDebugCodeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 076b5d628dfe83decdbbe2f5e74c50e08262c580
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700688"
---
# <a name="icordebugcodeenumnext-method"></a>ICorDebugCodeEnum::Next 方法

從列舉中取得指定數目的 "ICorDebugCode" 實例，從目前位置開始。

## <a name="syntax"></a>語法

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a>參數

 `celt`  
 在要抓取的 @no__t 0 實例數目。

 `values`  
 脫銷指標陣列，其中每一個都會指向 @no__t 0 物件。

 `pceltFetched`  
 脫銷實際傳回的 @no__t 0 實例數目的指標。 如果 `celt` 是一個，這個值可能會是 null。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** CorDebug.idl、CorDebug.h

 **LIBRARY:** CorGuids.lib

 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
 
