---
title: "ICorDebugStepper::Step 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.Step
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f921725d6794f08530a537462208264ced1dc089
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step 方法
導致此 ICorDebugStepper 單一步驟其包含的執行緒，以及 （選擇性） 若要繼續逐步執行緒內呼叫的函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bStepIn`  
 [in]設定為`true`逐步執行至呼叫的執行緒內的函式。 設定為`false`進入函式。  
  
## <a name="remarks"></a>備註  
 Common language runtime 會執行下一個 managed 的指令此 stepper 框架中時，就會完成的步驟。 如果`Step`是 stepper 上呼叫，不在 managed 程式碼中，步驟將在下一個 managed 程式碼指令由執行緒執行時完成。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
