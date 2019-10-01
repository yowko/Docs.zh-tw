---
title: ICorDebugCode::IsIL 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a81f4a53954c559ab12e27bcf039b7b1a1804cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700787"
---
# <a name="icordebugcodeisil-method"></a>ICorDebugCode::IsIL 方法

取得值，指出這個 "ICorDebugCode" 是否代表以 Microsoft 中繼語言（MSIL）編譯的程式碼。

## <a name="syntax"></a>語法

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a>參數
 `pbIL`  
 [out] `true`，如果這個 `ICorDebugCode` 代表以 MSIL 編譯的程式碼，則為，否則，`false`。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  

 **標頭：** CorDebug.idl、CorDebug.h  

 **LIBRARY:** CorGuids.lib  

 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
 
