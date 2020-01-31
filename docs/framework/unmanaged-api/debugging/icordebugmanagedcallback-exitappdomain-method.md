---
title: ICorDebugManagedCallback::ExitAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: 7bfa71ccff4a65e72a6b548a09d27648b67c0ae5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781846"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a>ICorDebugManagedCallback::ExitAppDomain 方法
通知偵錯工具，應用程式域已結束。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a>參數  
 `pProcess`  
 在ICorDebugProcess 物件的指標，代表包含指定之應用程式域的進程。  
  
 `pAppDomain`  
 在ICorDebugAppDomain 物件的指標，表示已結束的應用程式域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
