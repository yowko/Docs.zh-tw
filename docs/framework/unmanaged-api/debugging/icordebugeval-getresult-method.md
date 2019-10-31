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
ms.openlocfilehash: 52bfe669d3b078657916554255a11cecfc07d484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085081"
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
 只有在評估完成後，`GetResult` 方法才有效。  
  
 如果評估正常完成，`ppResult` 會指定結果。 如果它以例外狀況結束，則結果會擲回例外狀況。 如果是新物件的評估，則結果會是新物件的參考。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
