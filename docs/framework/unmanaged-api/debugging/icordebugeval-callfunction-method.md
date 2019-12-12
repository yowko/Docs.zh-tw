---
title: ICorDebugEval::CallFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: 4ac26ef4449dc02230f26b1247616b4587d217b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085163"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction 方法

設定對指定函數的呼叫。

這個方法在 .NET Framework 版本2.0 中已過時。 請改用[ICorDebugEval2：： CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) 。

## <a name="syntax"></a>語法

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a>參數

`pFunction`\
在ICorDebugFunction 物件的指標，指定要呼叫的函式。

`nArgs`\
在函數的引數數目。

`ppArgs`\
在指標的陣列，其中每一個都會指向 ICorDebugValue 物件，以指定要傳遞給函數的引數。

## <a name="remarks"></a>備註

如果函式是虛擬的，`CallFunction` 將會執行虛擬分派。 如果函式在不同的應用程式域中，只要所有引數也在該應用程式域中，就會發生轉換。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：** 1.1、1。0

## <a name="see-also"></a>請參閱

- [CallParameterizedFunction 方法](icordebugeval2-callparameterizedfunction-method.md)
