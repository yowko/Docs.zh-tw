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
ms.openlocfilehash: 04c36d1e5f0e79b71963683a3b613a9ad7392bcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125531"
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
在要抓取 `ICorDebugCode` 實例的數目。

`values`  
脫銷指標陣列，其中每一個都會指向 `ICorDebugCode` 物件。

`pceltFetched`  
脫銷實際傳回的 `ICorDebugCode` 實例數目的指標。 如果 `celt` 是一個，這個值可能會是 null。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
