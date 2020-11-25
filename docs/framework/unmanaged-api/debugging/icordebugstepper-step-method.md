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
ms.openlocfilehash: 234705e4495a1a582f3801ad1e645f923cd6f4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727688"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step 方法

讓這個 ICorDebugStepper 能以單一步驟完成其包含的執行緒，並選擇性地透過線上程中呼叫的函式繼續進行單一逐步執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>參數  

 `bStepIn`  
 在將設定為，逐步執行在 `true` 執行緒中呼叫的函式。 設定為 `false` 以不進入函數。  
  
## <a name="remarks"></a>備註  

 當 common language runtime 在這個分檔器的框架中執行下一個 managed 指令時，會完成此步驟。 如果 `Step` 在不在 managed 程式碼中的分檔器上呼叫，則會線上程執行下一個 managed 程式碼指令時完成此步驟。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
