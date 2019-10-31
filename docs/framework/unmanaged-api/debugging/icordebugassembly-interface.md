---
title: ICorDebugAssembly 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
ms.openlocfilehash: dea3231e3bbb361b56254756c6d99b115f73e792
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133962"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly 介面

表示組件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateModules 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|取得元件中所含模組的列舉值。|  
|[GetAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|取得包含這個 `ICorDebugAssembly` 實例之應用程式域的介面指標。|  
|[GetCodeBase 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|未在目前的 .NET Framework 版本中執行。|  
|[GetName 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|取得組件名稱。|  
|[GetProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|取得元件正在其中執行的 ICorDebugProcess 實例。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
