---
title: ICorDebugProcess::EnableLogMessages 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b199d3226ec391fadc356b5efacdbf10a3e25adf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766166"
---
# <a name="icordebugprocessenablelogmessages-method"></a>ICorDebugProcess::EnableLogMessages 方法
啟用和停用偵錯工具的記錄檔訊息的傳輸。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a>參數  
 `fOnOff`  
 [in]`true`啟用傳輸記錄檔訊息;`false`停用傳輸。  
  
## <a name="remarks"></a>備註  
 這個方法會有效之後，才[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼，就會發生。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
