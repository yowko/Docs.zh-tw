---
title: ICorDebugStepper::SetRangeIL 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610225708bf990850fce73d6d7ff66c556e24e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760600"
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL 方法
設定值，這個值，指定是否呼叫[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)值相對於原生程式碼，或相對於 Microsoft intermediate language (MSIL) 程式碼正在逐步執行方法的引數傳遞透過。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>參數  
 `bIL`  
 [in]若要設定`true`以指定的範圍相對於 MSIL 程式碼。 若要設定`false`以指定的範圍相對於原生程式碼。 預設值為 `true`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
