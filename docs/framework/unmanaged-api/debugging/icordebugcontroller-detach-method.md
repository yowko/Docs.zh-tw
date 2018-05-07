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
ms.openlocfilehash: cad8b305de580ce7cf4876939b95cc05d0fd11f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach 方法
從處理序或應用程式網域偵錯工具會中斷連結。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>備註  
 處理序或應用程式網域執行會繼續正常進行，但是"ICorDebugProcess"或"ICorDebugAppDomain"物件不再有效，而且沒有進一步的回呼就會發生。  
  
 在.NET Framework 2.0 版中，如果已啟用 unmanaged 偵錯，這個方法將會失敗由於作業系統限制。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 
