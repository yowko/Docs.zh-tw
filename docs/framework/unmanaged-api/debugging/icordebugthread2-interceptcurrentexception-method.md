---
title: ICorDebugThread2::InterceptCurrentException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f417fcd001d9e442ae518dbcd9df26eecb6efae9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException 方法
可讓偵錯工具攔截此執行緒上目前的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pFrame`  
 [in]ICorDebugFrame 表示作用中堆疊框架指標。  
  
## <a name="remarks"></a>備註  
 `InterceptCurrentException`方法呼叫之間的例外狀況回呼 ([icordebugmanagedcallback:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)或[icordebugmanagedcallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) 和相關聯的呼叫[Icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
