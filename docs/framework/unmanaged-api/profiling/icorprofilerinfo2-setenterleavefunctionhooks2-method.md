---
title: "ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c460cfd24a83ca2a6c75e061b7a797c8f455bc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 方法
指定程式碼剖析工具實作函式上更新版本的 「 輸入 」、 「 保留 」 和 「 tailcall"攔截 managed 函式的呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>參數  
 `pFuncEnter`  
 [in]指向要做為實作[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)回呼。  
  
 `pFuncLeave`  
 [in]指向要做為實作[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)回呼。  
  
 `pFuncTailcall`  
 [in]指向要做為實作[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)回呼。  
  
## <a name="remarks"></a>備註  
 `SetEnterLeaveFunctionHooks2`方法很類似[icorprofilerinfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)方法。 以指定要做為輸入/保持/tailcall 回呼和後者的較新版本以指定要做為輸入/保持/tailcall 回呼較舊版本的函式的函式使用前者。  
  
 一次只能有一組的回呼可能作用中。 因此，如果程式碼剖析工具呼叫兩者`ICorProfilerInfo::SetEnterLeaveFunctionHooks`和`SetEnterLeaveFunctionHooks2`，`SetEnterLeaveFunctionHooks2`用。  
  
 `SetEnterLeaveFunctionHooks2`方法可能只會從程式碼剖析工具呼叫[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
