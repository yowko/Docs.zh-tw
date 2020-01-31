---
title: ICorProfilerInfo3::SetFunctionIDMapper2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 107f596801832809e64088c85540c441e66189cf
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868469"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a>ICorProfilerInfo3::SetFunctionIDMapper2 方法
指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。 這個方法會以額外的資料參數擴充[ICorProfilerInfo：： SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)方法，而分析工具可能會使用它來區分執行時間。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a>參數  
 `pFunc`  
 在將呼叫以將 `FunctionID` 值對應至其替代值的[FunctionIDMapper2](functionidmapper2-function.md)執行的指標。  
  
 `clientData`  
 在傳遞至目前執行時間所進行之每個[FunctionIDMapper2](functionidmapper2-function.md)函式呼叫的指標。 分析工具可以使用此資訊來區分執行時間。  
  
## <a name="return-value"></a>傳回值  
  
## <a name="remarks"></a>備註  
 FunctionID 值的替代專案會傳遞至分析工具的函式進入/結束攔截器（[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)和[FunctionTailcall3](functiontailcall3-function.md) [; 或是 FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)和[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)），這是由[SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)或[SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)方法所指定。  
  
 `FunctionIDMapper2` 方法只能設定一次;我們建議您在[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼中設定它。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
