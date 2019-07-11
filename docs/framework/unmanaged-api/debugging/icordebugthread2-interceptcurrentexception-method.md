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
ms.openlocfilehash: a59476728280e42f45c416b614e6a721efaf26c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765254"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>ICorDebugThread2::InterceptCurrentException 方法
可讓偵錯工具攔截目前的例外狀況，在此執行緒。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a>參數  
 `pFrame`  
 [in]ICorDebugFrame，表示作用中堆疊框架指標。  
  
## <a name="remarks"></a>備註  
 `InterceptCurrentException`之間的例外狀況的回呼，可以呼叫方法 ([icordebugmanagedcallback:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)或是[ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)) 和相關聯的呼叫來[Icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
