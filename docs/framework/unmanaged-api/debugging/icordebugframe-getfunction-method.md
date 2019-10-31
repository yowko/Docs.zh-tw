---
title: ICorDebugFrame::GetFunction 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 39175e338e4fd98dd4af1325138da732ed81c764
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137913"
---
# <a name="icordebugframegetfunction-method"></a>ICorDebugFrame::GetFunction 方法
取得包含與此堆疊框架相關聯之程式碼的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppFunction`  
 脫銷ICorDebugFunction 物件位址的指標，代表包含與此堆疊框架相關聯之程式碼的函式。  
  
## <a name="remarks"></a>備註  
 如果框架未與任何特定的函式相關聯，`GetFunction` 方法可能會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
