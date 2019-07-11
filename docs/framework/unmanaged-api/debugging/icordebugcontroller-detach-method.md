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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f687e48413cb227ad715720e24bd645065309553
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748852"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach 方法
中斷連結處理序或應用程式定義域與偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>備註  
 處理序或應用程式網域執行會繼續正常執行，但 「 ICorDebugProcess"或"ICorDebugAppDomain 「 物件已不再有效，就會發生任何進一步的回呼。  
  
 在.NET Framework 2.0 版中，如果已啟用 unmanaged 偵錯，這個方法將會失敗由於作業系統限制。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
