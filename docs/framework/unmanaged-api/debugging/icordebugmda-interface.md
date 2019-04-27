---
title: ICorDebugMDA 介面
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916665"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA 介面
表示 Managed 偵錯助理 (MDA) 訊息。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetDescription 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|取得字串，包含此 MDA 的描述。|  
|[GetFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|取得與這個 MDA 相關聯的旗標。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|取得字串，包含此 MDA 的名稱。|  
|[GetOSThreadId 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|取得此 MDA 賴以執行的作業系統執行緒識別碼。|  
|[GetXML 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|取得與這個 MDA 相關聯的完整 XML 資料流。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
