---
title: ICorDebugStepper::Step 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137523"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step 方法
使此 ICorDebugStepper 逐步執行其包含的執行緒，並選擇性地繼續透過線上程內呼叫的函式進行單一逐步執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>參數  
 `bStepIn`  
 在設定為 `true`，以逐步執行線上程內呼叫的函式。 設定為 [`false`] 以不進入函式。  
  
## <a name="remarks"></a>備註  
 當 common language runtime 在這個分檔器的框架中執行下一個 managed 指令時，就會完成此步驟。 如果在不是 managed 程式碼的分檔器上呼叫 `Step`，當執行緒執行下一個 managed 程式碼指令時，步驟就會完成。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
