---
title: ICorDebugManagedCallback::CreateAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdac4b5b7a4a64a5fc939a7d35718ef276717fe7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a>ICorDebugManagedCallback::CreateAppDomain 方法
告知偵錯工具已建立應用程式定義域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProcess`  
 [in]表示所建立的應用程式定義域中的程序的 ICorDebugProcess 物件指標。  
  
 `pAppDomain`  
 [in]表示已建立的應用程式定義域的 ICorDebugAppDomain 物件指標。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
