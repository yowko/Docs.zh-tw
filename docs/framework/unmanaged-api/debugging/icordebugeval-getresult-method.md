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
ms.openlocfilehash: 2d065d956319076d3b92eddafd4a2c25ffbfbac1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976261"
---
# <a name="icordebugevalgetresult-method"></a>ICorDebugEval::GetResult 方法
取得此評估的結果。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppResult`  
 脫銷ICorDebugValue 物件位址的指標，如果評估正常完成，表示此評估的結果。  
  
## <a name="remarks"></a>備註  
 只有`GetResult`在評估完成後，方法才有效。  
  
 如果評估正常完成， `ppResult`會指定結果。 如果它以例外狀況結束，則結果會擲回例外狀況。 如果是新物件的評估，則結果會是新物件的參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
