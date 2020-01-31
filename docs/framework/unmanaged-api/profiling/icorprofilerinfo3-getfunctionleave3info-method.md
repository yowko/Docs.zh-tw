---
title: ICorProfilerInfo3::GetFunctionLeave3Info 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
ms.openlocfilehash: 0d3b93a293d4dda9dfe7b576708c832de2e25869
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862395"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a>ICorProfilerInfo3::GetFunctionLeave3Info 方法
提供[FunctionLeave3WithInfo](functionleave3withinfo-function.md)函式函式所回報給分析工具的函式之堆疊框架和傳回值。 只能在 `FunctionLeave3WithInfo` 回呼期間呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 在傳回之函數的 `FunctionID`。  
  
 `eltInfo`  
 [in] 代表特定堆疊框架之資訊的不透明控制代碼。 分析工具應該提供[FunctionLeave3WithInfo](functionleave3withinfo-function.md)函式所指定給 profiler 的相同 `eltInfo`。  
  
 `pFrameInfo`  
 [out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。 此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionLeave3Info` 方法的 `FunctionLeave3WithInfo` 回呼中有效。  
  
 `pRetvalRange`  
 脫銷[COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)結構的指標，其中包含從函數傳回的值。 若要存取傳回值資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_RETVAL` 旗標。 分析工具可以使用[ICorProfilerInfo：： SetEventMask 方法](icorprofilerinfo-seteventmask-method.md)來設定事件旗標。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
