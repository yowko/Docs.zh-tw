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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66e51dc15f7d44ede26634571fa04c58e9735694
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934767"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction 方法

設定指定的函式的呼叫。

這個方法是在.NET Framework 2.0 版中已過時。 使用[ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md)改。

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
[in]ICorDebugFunction 物件，指定要呼叫的函式的指標。

`nArgs`\
[in]函式的引數數目。

`ppArgs`\
[in]指標的陣列，其中每一個指向 ICorDebugValue 物件，指定要傳遞至函式的引數。

## <a name="remarks"></a>備註

如果函式是虛擬的`CallFunction`會執行虛擬分派。 如果函式不同的應用程式定義域中，則會發生轉換，只要所有引數也是應用程式定義域中。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**LIBRARY:** CorGuids.lib

**.NET framework 版本：** 1.1, 1.0

## <a name="see-also"></a>另請參閱

- [CallParameterizedFunction 方法](icordebugeval2-callparameterizedfunction-method.md)