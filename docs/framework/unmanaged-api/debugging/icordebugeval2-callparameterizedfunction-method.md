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
ms.openlocfilehash: c36dec80b6885b0ee56670b94dbd0b155a9710b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729703"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction 方法

設定指定之 ICorDebugFunction 的呼叫，此呼叫可以嵌套在其函式採用參數的類別內 <xref:System.Type> ，或本身可以接受 <xref:System.Type> 參數。  
  
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
 在 `ICorDebugFunction` 物件的指標，代表要呼叫的函式。  
  
 `nTypeArgs`  
 在函數所採用的引數數目。  
  
 `ppTypeArgs`  
 在指標的陣列，每個指標都會指向表示函式引數的 ICorDebugType 物件。  
  
 `nArgs`  
 在函數中傳遞的值數目。  
  
 `ppArgs`  
 在指標的陣列，每個指標都會指向表示函式引數中傳遞之值的 ICorDebugValue 物件。  
  
## <a name="remarks"></a>備註  

 `CallParameterizedFunction` 類似于 [ICorDebugEval：： CallFunction](icordebugeval-callfunction-method.md) ，不同之處在于函式可能在具有型別參數的類別內、本身可以採用型別參數或兩者。 應先為類別指定型別引數，然後為函式提供型別引數。  
  
 如果函式在不同的應用程式域中，就會發生轉換。 但是，所有型別和值引數都必須在目標應用程式域中。  
  
 函數評估只能在有限的情況下執行。 如果 `CallParameterizedFunction` 或 `ICorDebugEval::CallFunction` 失敗，傳回的 HRESULT 將會指出失敗的最普遍可能原因。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
