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
ms.openlocfilehash: 493b4850436b3724287210878992d1d8ce8fe168
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589395"
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction 方法
設定指定的函式的呼叫。  
  
 這個方法是在.NET Framework 2.0 版中已過時。 使用[ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)改。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFunction`  
 [in]ICorDebugFunction 物件，指定要呼叫的函式的指標。  
  
 `nArgs`  
 [in]函式的引數數目。  
  
 `ppArgs`  
 [in]指標的陣列，其中每一個指向 ICorDebugValue 物件，指定要傳遞至函式的引數。  
  
## <a name="remarks"></a>備註  
 如果函式是虛擬的`CallFunction`會執行虛擬分派。 如果函式不同的應用程式定義域中，則會發生轉換，只要所有引數也是應用程式定義域中。  
  
## <a name="requirements"></a>需求  
 **平台：** WindowSee[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1, 1.0  
  
## <a name="see-also"></a>另請參閱
- [CallParameterizedFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
