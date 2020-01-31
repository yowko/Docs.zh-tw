---
title: ICoreClrDebugTarget 介面
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 190671b4f690f8c2cad43cf446a1196985ec5a42
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790744"
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget 介面
提供方法來控制參考計數、列舉進程，以及釋放與附加至遠端 Macintosh Silverlight 目標的偵錯工具相關聯的記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
|方法|描述|  
|------------|-----------------|  
|[ICoreClrDebugTarget::EnumProcesses 方法](icoreclrdebugtarget-enumprocesses-method.md)|列舉在遠端電腦上執行的處理序。|  
|[ICoreClrDebugTarget::EnumRuntimes 方法](icoreclrdebugtarget-enumruntimes-method.md)|列舉遠端電腦上指定之進程中的 common language runtime （CLRs）。|  
|[ICoreClrDebugTarget::FreeMemory 方法](icoreclrdebugtarget-freememory-method.md)|釋放這個類別中的列舉方法所配置的記憶體。|  
  
## <a name="remarks"></a>備註  
 目前，只有針對在遠端 Macintosh 電腦上執行的 Silverlight 應用程式目標進行偵測時，才支援這種功能。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CoreClrRemoteDebuggingInterfaces。h  
  
 連結**庫：** mscordbi_macx86 .dll  
  
 **.NET Framework 版本：** 3.5 SP1  
  
## <a name="see-also"></a>請參閱

- [ICorDebugRemoteTarget 介面](icordebugremotetarget-interface.md)
- [ICorDebug 介面](icordebug-interface.md)

- [偵錯介面](debugging-interfaces.md)
