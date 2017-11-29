---
title: "ICoreClrDebugTarget 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e13355078727a55c950bed795d3b01b6c7d52564
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget 介面
提供方法來控制參考計數、 列舉處理序，並釋放與偵錯工具附加至遠端的 Macintosh Silverlight 目標相關聯的記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[Icoreclrdebugtarget:: Enumprocesses 方法](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|列舉在遠端電腦上執行的處理序。|  
|[Icoreclrdebugtarget:: Enumruntimes 方法](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|列舉的 common language runtime (Clr) 中指定的處理序的遠端電腦上。|  
|[Icoreclrdebugtarget:: Freememory 方法](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|釋放由這個類別中的列舉型別方法所配置的記憶體。|  
  
## <a name="remarks"></a>備註  
 目前，這項功能僅適用於偵錯遠端的 Macintosh 電腦執行的 Silverlight 架構應用程式目標支援。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces.h  
  
 **程式庫：** mscordbi_macx86.dll  
  
 **.NET framework 版本：** 3.5 SP1  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugRemoteTarget 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
