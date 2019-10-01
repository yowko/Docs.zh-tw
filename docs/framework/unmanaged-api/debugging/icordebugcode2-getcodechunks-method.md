---
title: ICorDebugCode2::GetCodeChunks 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bdaf6391ca5c19f073708d6258ad5775bec9824
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700734"
---
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks 方法

取得此程式碼物件所組成的程式碼區塊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a>參數

 `cbufSize`  
 在@No__t-0 陣列的大小。

 `pcnumChunks`  
 脫銷@No__t-0 陣列中傳回的區塊數目。

 `chunks`  
 脫銷"CodeChunkInfo" 結構的陣列，其中每一個都代表一個程式碼區塊。 如果 `cbufSize` 的值為0，則這個參數可以是 null。

## <a name="remarks"></a>備註

 程式碼區塊永遠不會重迭，而且它們會遵循[ICorDebugCode：： GetCode](icordebugcode-getcode-method.md)串連的順序。 .NET Framework 版本2.0 中的 Microsoft 中繼語言（MSIL）程式碼物件將會包含單一程式碼區塊。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** CorDebug.idl、CorDebug.h

 **LIBRARY:** CorGuids.lib

 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
 
