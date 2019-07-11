---
title: ICorDebugStepper::SetInterceptMask 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37b644227a6085352bed682f0ddd7c3455b54895
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760699"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask 方法
設定值，這個值會指定逐步執行的程式碼類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>參數  
 `mask`  
 [in]CorDebugIntercept 列舉，指定的程式碼的類型值的組合。  
  
## <a name="remarks"></a>備註  
 如果設定的位元為攔截器，在遇到攔截程式碼的指定型別時，將會完成步進。 位元會清除，如果攔截程式碼將會略過。  
  
 `SetInterceptMask`方法可能會有非預期的互動[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) （從使用者的觀點來看）。 比方說，如果只顯示 (亦即，非內部) 類別初始化程式碼的一部分缺少對應資訊，且未設定 STOP_NO_MAPPING_INFO (請參閱[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)方法，CorDebugUnmappedStop 列舉） 步進會不進入類別初始設定。 根據預設，只有 INTERCEPT_NONE 值`CorDebugIntercept`將用於列舉型別。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
