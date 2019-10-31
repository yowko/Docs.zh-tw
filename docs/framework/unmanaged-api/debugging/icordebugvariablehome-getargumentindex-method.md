---
title: ICorDebugVariableHome：： GetArgumentIndex 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 86b2815c6f95c674c49bba7455e8497192bd8bac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125145"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>ICorDebugVariableHome：： GetArgumentIndex 方法

取得函數引數的索引。

## <a name="syntax"></a>語法

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>參數

`pArgumentIndex`\
脫銷引數索引的指標。

## <a name="return-value"></a>傳回值

方法會傳回下列值。

|值|描述|
|-----------|-----------------|
|`S_OK`|方法呼叫傳回有效的引數索引。|
|`E_FAIL`|目前的[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)實例代表本機變數。|

## <a name="remarks"></a>備註

引數索引可以用來抓取此引數的中繼資料。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>請參閱

- [ICorDebugVariableHome 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
