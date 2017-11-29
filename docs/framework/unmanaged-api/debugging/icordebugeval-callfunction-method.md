---
title: "ICorDebugEval::CallFunction 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CallFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72713d81931b53e8d61fb39cee146fd30a59bfcc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction 方法
設定指定函式的呼叫。  
  
 這個方法是.NET Framework 2.0 版中已過時。 使用[icordebugeval2:: Callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)改為。  
  
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
 [in]ICorDebugFunction 物件，指定要呼叫的函式指標。  
  
 `nArgs`  
 [in]函式的引數數目。  
  
 `ppArgs`  
 [in]指標的陣列，其中每個指向 ICorDebugValue 物件，指定要傳遞至函數的引數。  
  
## <a name="remarks"></a>備註  
 如果函式是虛擬的`CallFunction`將執行虛擬分派。 如果函式不同的應用程式網域中，則會發生轉換，只要所有引數也是應用程式定義域中。  
  
## <a name="requirements"></a>需求  
 **平台：** WindowSee[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1、 1.0  
  
## <a name="see-also"></a>另請參閱  
 [CallParameterizedFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
