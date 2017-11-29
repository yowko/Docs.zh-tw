---
title: "ICorProfilerFunctionControl::SetCodegenFlags 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetCodegenFlags
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: eb212b0fb777e960d7121dadaf4715b44306db6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags 方法
設定從一或多個旗標[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列舉來控制產生程式碼的 just-in-time (JIT) 重新編譯函式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
#### <a name="parameters"></a>參數  
 `flags`  
 [in]從一或多個旗標[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列舉型別。  
  
## <a name="remarks"></a>備註  
 分析工具取得透過此介面的執行個體[icorprofilercallback4:: Getrejitparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)回呼。 `SetCodegenFlags`可讓程式碼剖析工具，來控制重新編譯函式的程式碼產生。 如同其他所有的 JIT 重新編譯參數的程式碼產生旗標會套用至函式的所有執行個體。  
  
 JIT 編譯器會考慮這些編譯旗標，以及編譯函式時，由其他來源中，指定其他旗標。  其他來源包括偵錯工具、 全域旗標設定在由啟動分析工具使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法 (具有值`COR_PRF_DISABLE_INLINING`和`COR_PRF_DISABLE_OPTIMIZATIONS`)，和 profiler [Icorprofilercallback:: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回呼。  JIT 編譯器會提供要求最少的最佳化的來源的優先順序。  例如，如果分析工具指定`COR_PRF_DISABLE_INLINING`在啟動時，但未指定`COR_PRF_CODEGEN_DISABLE_INLINING`中[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)回呼，內嵌仍會停用。  同樣地，如果未指定分析工具`COR_PRF_CODEGEN_DISABLE_INLINING`中`SetCodegenFlags`，但然後停用內嵌使用[icorprofilercallback:: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回呼，內嵌已停用。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerFunctionControl 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
