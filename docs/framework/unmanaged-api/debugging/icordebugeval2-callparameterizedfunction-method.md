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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77d9ec0cf1cbca63382e7f29de85c2f9566dc2bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416162"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction 方法
設定指定 ICorDebugFunction，可以巢狀的類別的建構函式會採用內部呼叫<xref:System.Type>參數或本身可以採取<xref:System.Type>參數。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFunction`  
 [in]指標`ICorDebugFunction`物件，代表要呼叫的函式。  
  
 `nTypeArgs`  
 [in]函式的引數數目。  
  
 `ppTypeArgs`  
 [in]指標的陣列，其中每個指向 ICorDebugType 物件，表示函式引數。  
  
 `nArgs`  
 [in]函式中，傳遞的值數目。  
  
 `ppArgs`  
 [in]指標陣列，其中每個指向 ICorDebugValue 物件，表示值傳入函式引數。  
  
## <a name="remarks"></a>備註  
 `CallParameterizedFunction` 就像[icordebugeval:: Callfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)不同之處在於函式可能具有型別參數的類別內，可能本身需要型別參數，或兩者。 針對類別，然後再針對函式，應該先指定型別引數。  
  
 如果函式是在不同的應用程式網域中，則會發生轉換。 不過，所有類型和值的引數必須都是目標應用程式定義域中。  
  
 只在少數情況下，可以執行函式評估。 如果`CallParameterizedFunction`或`ICorDebugEval::CallFunction`失敗，傳回的 HRESULT 會指出失敗最常見的可能原因。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
