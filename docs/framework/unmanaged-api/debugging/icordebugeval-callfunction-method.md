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
ms.openlocfilehash: 1cf0080945ad78565fae3fedb454ceba7825cb4a
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976235"
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

如果函式是虛擬的`CallFunction` ，將會執行虛擬分派。 如果函式在不同的應用程式域中，只要所有引數也在該應用程式域中，就會發生轉換。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：** 1.1、1。0

## <a name="see-also"></a>另請參閱

- [CallParameterizedFunction 方法](icordebugeval2-callparameterizedfunction-method.md)
