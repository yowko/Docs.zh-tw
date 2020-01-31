---
title: ICorProfilerInfo4::EnumJITedFunctions2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
ms.openlocfilehash: 3903ebf1ad35bd7eb1ba49b4f1acda9024678423
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862200"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2 方法
傳回先前已進行 JIT 編譯和 JIT 重新編譯之所有函式的列舉值。 這個方法會取代[ICorProfilerInfo3：： EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)方法，這不會列舉 JIT 重新編譯的識別碼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>參數  
 `ppEnum`  
 脫銷[ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md)列舉值的指標。  
  
## <a name="remarks"></a>備註  
 這個方法可能會與 `JITCompilation` 回呼（例如[ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)方法）重迭。 傳回的列舉包含 `COR_PRF_FUNCTION::reJitId` 欄位的值。 這個方法取代的[ICorProfilerInfo3：： EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)方法不會列舉 JIT 重新編譯的識別碼，因為 `COR_PRF_FUNCTION::reJitId` 欄位一律設定為0。 `ICorProfilerInfo4::EnumJITedFunctions` 方法會列舉 JIT 重新編譯的識別碼，因為已正確設定 `COR_PRF_FUNCTION::reJitId` 欄位。 請注意， [ICorProfilerInfo4：： EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md)方法可以觸發垃圾收集，而[ICorProfilerInfo3：： EnumJITedFunctions 方法](icorprofilerinfo3-enumjitedfunctions-method.md)則不會。  如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [EnumJITedFunctions 方法](icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
