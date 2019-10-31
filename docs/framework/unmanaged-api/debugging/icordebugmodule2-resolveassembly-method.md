---
title: ICorDebugModule2::ResolveAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: 0809a149a5a5a5e9adea059140d7b4b456337ef3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125310"
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly 方法

解析指定的元資料標記所參考的元件。

## <a name="syntax"></a>語法

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a>參數

`tkAssemblyRef`\
在參考元件的 `mdToken` 值。

`ppAssembly`\
脫銷表示元件之 ICorDebugAssembly 物件的位址指標。

## <a name="remarks"></a>備註

如果在呼叫 `ResolveAssembly` 時尚未載入元件，則會傳回 CORDBG_E_CANNOT_RESOLVE_ASSEMBLY 的 HRESULT 值。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
