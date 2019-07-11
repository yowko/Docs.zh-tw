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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dde27f74ac59d033b6e25fba1dbb8e52c4b91af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760684"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive 方法
取得值，指出此 ICorDebugStepper 目前是否正在執行的步驟。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>參數  
 `pbActive`  
 [out]會傳回`true`步進目前正在執行的步驟; 否則會傳回`false`。  
  
## <a name="remarks"></a>備註  
 任何步驟動作維持作用，直到偵錯工具收到[icordebugmanagedcallback:: Stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)呼叫，這會自動停用步進。 步進可能也會停用不當藉由呼叫[icordebugstepper:: Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)在回呼之前條件為止。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
