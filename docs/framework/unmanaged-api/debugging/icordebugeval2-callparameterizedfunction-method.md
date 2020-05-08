---
title: ICorDebugEval2::CallParameterizedFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: 72bcc2479f7b6f41b384fc2517f0b04694663398
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976144"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction 方法
設定對指定 ICorDebugFunction 的呼叫，其可以嵌套在類別中，其會採用<xref:System.Type>參數，或本身可接受<xref:System.Type>參數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>參數  
 `pFunction`  
 在物件的指標， `ICorDebugFunction`代表要呼叫的函式。  
  
 `nTypeArgs`  
 在函式所採用的引數數目。  
  
 `ppTypeArgs`  
 在指標陣列，其中每一個都會指向代表函式引數的 ICorDebugType 物件。  
  
 `nArgs`  
 在函數中傳遞的值數目。  
  
 `ppArgs`  
 在指標的陣列，其中每一個都會指向 ICorDebugValue 物件，代表在函數引數中傳遞的值。  
  
## <a name="remarks"></a>備註  
 `CallParameterizedFunction`類似于[ICorDebugEval：： CallFunction](icordebugeval-callfunction-method.md) ，但函式可能位於具有型別參數的類別內，本身可能會採用型別參數，或兩者都是。 應該先為類別指定類型引數，然後為函式提供。  
  
 如果函式在不同的應用程式域中，將會發生轉換。 不過，所有類型和值引數都必須在目標應用程式域中。  
  
 函數評估只能在有限的情況下執行。 如果`CallParameterizedFunction`或`ICorDebugEval::CallFunction`失敗，則傳回的 HRESULT 會指出失敗的最常見可能原因。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
