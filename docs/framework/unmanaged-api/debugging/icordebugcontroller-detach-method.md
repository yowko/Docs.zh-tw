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
ms.openlocfilehash: 55acb6e3ec60925cba3d8aa5328547c54f270356
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732667"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach 方法

卸離進程或應用程式域中的偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>備註  

 進程或應用程式域會繼續正常執行，但 "ICorDebugProcess" 或 "ICorDebugAppDomain" 物件不再有效，且不會再發生任何回呼。  
  
 在 .NET Framework 2.0 版中，如果已啟用非受控的偵錯工具，此方法將會因為作業系統限制而失敗。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
