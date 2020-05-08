---
title: ICorDebugController::Detach 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: 480fec4897dac73594515ba8bc0f0e96ceb79ace
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892907"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach 方法
從進程或應用程式域中卸離偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>備註  
 進程或應用程式域會繼續正常執行，但 "ICorDebugProcess" 或 "ICorDebugAppDomain" 物件不再有效，也不會再發生任何回呼。  
  
 在2.0 版的 .NET Framework 中，如果已啟用非受控的調試功能，此方法將會因為作業系統限制而失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
