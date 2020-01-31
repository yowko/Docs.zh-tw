---
title: ICorProfilerCallback::JITCompilationFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: f1cfef464569b577923fbb16624c99358998d29c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866243"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a>ICorProfilerCallback::JITCompilationFinished 方法
通知分析工具，及時（JIT）編譯器已完成編譯函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>參數

- `functionId`

  \[in] 已編譯之函式的識別碼。

- `hrStatus`

  \[in] 值，指出編譯是否成功。

- `fIsSafeToBlock`

  \[in] 值，指出封鎖器是否會影響執行時間的作業。 如果封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回，則此值為 `true`。否則，`false`。

  雖然 `true` 的值不會傷害執行時間，但它可能會扭曲分析結果。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [JITCompilationStarted 方法](icorprofilercallback-jitcompilationstarted-method.md)
