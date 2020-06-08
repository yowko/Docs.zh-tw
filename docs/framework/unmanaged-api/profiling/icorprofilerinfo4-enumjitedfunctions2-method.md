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
ms.openlocfilehash: 2c4a89d5f96ef572518f25bf58a0005454f8e3f0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496122"
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
 這個方法可能會與 `JITCompilation` 回呼（例如[ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)方法）重迭。 傳回的列舉包含欄位的值 `COR_PRF_FUNCTION::reJitId` 。 這個方法取代的[ICorProfilerInfo3：： EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)方法不會列舉 JIT 重新編譯的識別碼，因為 `COR_PRF_FUNCTION::reJitId` 欄位一律設定為0。 `ICorProfilerInfo4::EnumJITedFunctions`方法會列舉 JIT 重新編譯的識別碼，因為 `COR_PRF_FUNCTION::reJitId` 欄位已正確設定。 請注意， [ICorProfilerInfo4：： EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md)方法可以觸發垃圾收集，而[ICorProfilerInfo3：： EnumJITedFunctions 方法](icorprofilerinfo3-enumjitedfunctions-method.md)則不會。  如需詳細資訊，請參閱[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md)。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EnumJITedFunctions 方法](icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4 介面](icorprofilerinfo4-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
