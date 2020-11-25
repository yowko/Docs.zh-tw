---
title: ICorProfilerCallback::ModuleAttachedToAssembly 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: bcf5c5c9044a30fc8259dbc54bad8f3141f0f926
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733109"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly 方法

通知分析工具正在將模組附加至其父元件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a>參數  

 `moduleId`  
 在正在附加之模組的識別碼。  
  
 `AssemblyId`  
 在模組所附加之父元件的識別碼。  
  
## <a name="remarks"></a>備註  

 模組可以透過匯入位址表載入 (IAT) 、透過呼叫 `LoadLibrary` ，或透過中繼資料參考。 因此，common language runtime (CLR) 載入器有多個程式碼路徑，可用來判斷模組所在的元件。 因此，可能會在呼叫 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 之後，模組不知道它所在的元件，並無法取得父元件識別碼。 `ModuleAttachedToAssembly`當模組附加至其父元件且可以取得其父元件識別碼時，會呼叫方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
