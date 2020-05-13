---
title: ICorDebugModule::GetFunctionFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: a33b6ff308f3444496e5a1cb2e04f28e80305db5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212575"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a>ICorDebugModule::GetFunctionFromToken 方法
取得元資料標記所指定的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>參數  
 `methodDef`  
 在`mdMethodDef`參考函數中繼資料的元資料標記。  
  
 `ppFunction`  
 脫銷代表函式之 ICorDebugFunction 介面物件的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetFunctionFromToken`如果傳入的值 `methodDef` 未參考 Microsoft 中繼語言（MSIL）方法，此方法會傳回 CORDBG_E_FUNCTION_NOT_IL HRESULT。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
