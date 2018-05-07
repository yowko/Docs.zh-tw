---
title: ICorDebugEval::GetResult 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e160eddf667b542929c8dd3790de666a8e8bb77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult 方法
取得這項評估的結果。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppResult`  
 [out]ICorDebugValue 物件，表示這項評估的結果，如果評估正常完成的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetResult`完成評估之後，才是有效方法。  
  
 如果評估一般來說，完成`ppResult`指定的結果。 如果它所終止的例外狀況，則結果為擲回的例外狀況。 如果評估為新的物件，則結果會是新物件的參考。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
