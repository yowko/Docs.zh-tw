---
title: ICorProfilerInfo::SetFunctionIDMapper 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 52ab9a089b5def4f3db2f99abc5a718d66cca739
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863448"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a>ICorProfilerInfo::SetFunctionIDMapper 方法
指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a>參數  
 `pFunc`  
 在將呼叫以將 `FunctionID` 值對應至其替代值的[FunctionIDMapper](functionidmapper-function.md)執行的指標。  
  
## <a name="remarks"></a>備註  
 `FunctionID` 值的替代專案會傳遞至分析工具的函式進入/結束攔截器（[FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)和[FunctionTailcall2](functiontailcall2-function.md)），這是由[ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)方法所指定。  
  
 `FunctionIDMapper` 只能設定一次，建議您在[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼中加以設定。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
