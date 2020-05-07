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
ms.openlocfilehash: d9e2236b944137de82bb056820f81014febfcc5f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894902"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly 介面

表示組件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateModules 方法](icordebugassembly-enumeratemodules-method.md)|取得元件中所含模組的列舉值。|  
|[GetAppDomain 方法](icordebugassembly-getappdomain-method.md)|取得包含這個`ICorDebugAssembly`實例之應用程式域的介面指標。|  
|[GetCodeBase 方法](icordebugassembly-getcodebase-method.md)|未在目前的 .NET Framework 版本中執行。|  
|[GetName 方法](icordebugassembly-getname-method.md)|取得組件名稱。|  
|[GetProcess 方法](icordebugassembly-getprocess-method.md)|取得元件正在其中執行的 ICorDebugProcess 實例。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
