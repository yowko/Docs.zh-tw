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
ms.openlocfilehash: 814bf87039ef57056f13994af1b873f8f57c7804
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718211"
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
 在CorDebugIntercept 列舉值的組合，可指定程式碼的類型。  
  
## <a name="remarks"></a>備註  

 如果設定攔截器的位，則在遇到指定的攔截程式碼類型時，就會完成分檔器。 如果已清除此位，則會略過攔截程式碼。  
  
 `SetInterceptMask`從使用者的觀點來看，方法可能與[ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (之間的互動) 。 例如，如果唯一可見的 (（類別初始化程式碼的非內部) 部分缺少對應資訊，而且 STOP_NO_MAPPING_INFO 未設定 (請參閱 [ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) 方法和 CorDebugUnmappedStop 列舉) ，則分檔器將不會跳過類別初始化。 依預設，只 `CorDebugIntercept` 會使用列舉的 INTERCEPT_NONE 值。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
