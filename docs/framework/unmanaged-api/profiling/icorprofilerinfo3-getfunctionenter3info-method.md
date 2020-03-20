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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177016"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info 方法
提供[函數Enter3WithInfo](functionenter3withinfo-function.md)函數向探測器報告的函數的堆疊幀和參數資訊。 只能在 `FunctionEnter3WithInfo` 回呼期間呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [in] 正在輸入之函式的 `FunctionID`。  
  
 `eltInfo`  
 [in] 代表特定堆疊框架之資訊的不透明控制代碼。 探測器應提供與`eltInfo`[功能Enter3WithInfo](functionenter3withinfo-function.md)函數給出的相同。  
  
 `pFrameInfo`  
 [out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。 此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionEnter3Info` 方法的 `FunctionEnter3WithInfo` 回呼中有效。  
  
 `pcbArgumentInfo`  
 [進出]指向[COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)結構的總大小（以位元組為單位）的指標（加上 由`pArgumentInfo`指向的參數範圍的任何其他[COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)結構。 如果指定的大小不足，會傳回 ERROR_INSUFFICIENT_BUFFER，且預期大小會儲存在 `pcbArgumentInfo`。 若要呼叫 `GetFunctionEnter3Info` 以擷取預期的 `*pcbArgumentInfo` 值，請設定 `*pcbArgumentInfo`= 0 和 `pArgumentInfo`= NULL。  
  
 `pArgumentInfo`  
 [出]指向[COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)結構的指標，該結構按從左至右的順序描述函數參數在記憶體中的位置。  
  
## <a name="remarks"></a>備註  
 程式碼剖析工具必須配置足夠的空間供檢查中之函式的 `COR_PRF_FUNCTION_ARGUMENT_INFO` 結構使用，且必須在 `pcbArgumentInfo` 參數指出大小。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [功能輸入3與資訊](functionenter3withinfo-function.md)
- [功能離開3與資訊](functionleave3withinfo-function.md)
- [功能尾聲3與資訊](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [分析](index.md)
