---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b6f53d5747eca00b898b2cde66d75764ca490cf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772100"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a>ICorProfilerInfo::SetEnterLeaveFunctionHooks 方法
指定要呼叫 「 輸入 」、 「 保留 」 和 「 tailcall"勾點的受管理的函式的分析工具實作函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a>參數  
 `pFuncEnter`  
 [in]要做為實作的指標[FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)回呼。  
  
 `pFuncLeave`  
 [in]要做為實作的指標[FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)回呼。  
  
 `pFuncTailcall`  
 [in]要做為實作的指標[FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)回呼。  
  
## <a name="remarks"></a>備註  
 在.NET Framework 1.0 版中，每個函式指標可以是 null，以停用該對應的回呼。  
  
 只有一組回呼可以作用一次。 因此，如果程式碼剖析工具呼叫兩者`SetEnterLeaveFunctionHooks`並[ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，然後`SetEnterLeaveFunctionHooks2`會優先使用。  
  
 `SetEnterLeaveFunctionHooks`方法可以只從分析工具的呼叫[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
