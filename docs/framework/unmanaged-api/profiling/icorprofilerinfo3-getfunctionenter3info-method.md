---
title: ICorProfilerInfo3::GetFunctionEnter3Info 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a12e747344f4943dafced2402e0f08a08ac6e7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498227"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info 方法
提供給分析工具所報告的函式之堆疊框架和引數資訊[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)函式。 只能在 `FunctionEnter3WithInfo` 回呼期間呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
#### <a name="parameters"></a>參數  
 `functionId`  
 [in] 正在輸入之函式的 `FunctionID`。  
  
 `eltInfo`  
 [in] 代表特定堆疊框架之資訊的不透明控制代碼。 分析工具應該提供相同`eltInfo`它是給定[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)函式。  
  
 `pFrameInfo`  
 [out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。 此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionEnter3Info` 方法的 `FunctionEnter3WithInfo` 回呼中有效。  
  
 `pcbArgumentInfo`  
 [in、 out]大小總計，以位元組為單位的指標的[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)結構 (再加上任何額外[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) 所指向之引數範圍的結構`pArgumentInfo`). 如果指定的大小不足，會傳回 ERROR_INSUFFICIENT_BUFFER，且預期大小會儲存在 `pcbArgumentInfo`。 若要呼叫 `GetFunctionEnter3Info` 以擷取預期的 `*pcbArgumentInfo` 值，請設定 `*pcbArgumentInfo`= 0 和 `pArgumentInfo`= NULL。  
  
 `pArgumentInfo`  
 [out]指標[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)結構，描述在記憶體中左到右的順序的函式的引數的位置。  
  
## <a name="remarks"></a>備註  
 程式碼剖析工具必須配置足夠的空間供檢查中之函式的 `COR_PRF_FUNCTION_ARGUMENT_INFO` 結構使用，且必須在 `pcbArgumentInfo` 參數指出大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
