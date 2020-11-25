---
title: ICorDebugStepper::IsActive 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 0a57dfe5bb4dfdc08a5e3f2238da6794e62bd958
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718276"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive 方法

取得值，這個值表示此 ICorDebugStepper 目前是否正在執行步驟。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>參數  

 `pbActive`  
 擴展 `true` 如果分檔器目前正在執行步驟，則傳回，否則傳回 `false` 。  
  
## <a name="remarks"></a>備註  

 任何步驟動作都會保持作用中，直到偵錯工具收到 [ICorDebugManagedCallback：： StepComplete](icordebugmanagedcallback-stepcomplete-method.md) 呼叫，這會自動停用分檔器。 您也可以在達到回呼條件之前呼叫 [ICorDebugStepper：:D eactivate](icordebugstepper-deactivate-method.md) ，提前停用分檔器。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
