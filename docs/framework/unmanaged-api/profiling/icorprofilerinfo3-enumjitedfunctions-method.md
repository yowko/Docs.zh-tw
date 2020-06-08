---
title: ICorProfilerInfo3::EnumJITedFunctions 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: 3ebf4a7706b3d3495e4a617b4f86a50281115436
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496551"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a>ICorProfilerInfo3::EnumJITedFunctions 方法
傳回先前已進行 JIT 編譯之所有函式的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>參數  
 `ppEnum`  
 脫銷[ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md)列舉值的指標。  
  
## <a name="remarks"></a>備註  
 這個方法可能會與 `JITCompilation` 回呼（例如[ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)方法）重迭。 這個方法所傳回的列舉值不包含從 Ngen.exe 產生的原生映射載入的函式。  
  
> [!NOTE]
> 傳回的列舉只包含 "0" 代表欄位的值 `COR_PRF_FUNCTION::reJitId` 。  如果您需要有效 `COR_PRF_FUNCTION::reJitId` 的值，請使用[ICorProfilerInfo4：： EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md)方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
