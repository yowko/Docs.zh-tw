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
ms.openlocfilehash: 703f454f7ed1d2a959b761726f433db22cb73b01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791780"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive 方法
取得值，指出這個 ICorDebugStepper 目前是否正在執行步驟。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbActive`  
 脫銷如果分檔器目前正在執行步驟，則傳回 `true`;否則，會傳回 `false`。  
  
## <a name="remarks"></a>備註  
 任何步驟動作都會維持作用中狀態，直到偵錯工具收到[ICorDebugManagedCallback：： StepComplete](icordebugmanagedcallback-stepcomplete-method.md)呼叫，這會自動停用分檔器。 在達到回呼條件之前，也可以藉由呼叫[ICorDebugStepper：:D eactivate](icordebugstepper-deactivate-method.md) ，提前停用分檔器。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
