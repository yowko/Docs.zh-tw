---
title: ICorProfilerInfo3::GetFunctionTailcall3Info 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176990"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>ICorProfilerInfo3::GetFunctionTailcall3Info 方法
提供[函數尾聲3WithInfo](functiontailcall3withinfo-function.md)函數向探測器報告的函數的堆疊幀。 只能在 `FunctionTailcall3WithInfo` 回呼期間呼叫這個方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a>參數  
 `functionId`  
 [在]正在`FunctionID`返回的函數的 。  
  
 `eltInfo`  
 [in] 代表特定堆疊框架之資訊的不透明控制代碼。 探測器應提供`eltInfo``FunctionTailcall3WithInfo`函數提供給探測器的相同。  
  
 `pFrameInfo`  
 [out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。 此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionTailcall3Info` 方法的 `FunctionTailcall3WithInfo` 回呼中有效。  
  
## <a name="remarks"></a>備註  
  
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
