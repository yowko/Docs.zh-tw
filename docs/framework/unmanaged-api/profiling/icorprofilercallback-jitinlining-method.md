---
title: ICorProfilerCallback::JITInlining 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866205"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining 方法
通知分析工具，及時（JIT）編譯器即將以另一個函式插入函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>參數  
 `callerId`  
 在將插入 `calleeId` 函式的函式識別碼。  
  
 `calleeId`  
 在要插入之函式的識別碼。  
  
 `pfShouldInline`  
 [out] 允許進行插入的 `true`;否則，`false`。  
  
## <a name="remarks"></a>備註  
 分析工具可以將 `pfShouldInline` 設定為 `false`，以防止 `calleeId` 函式插入 `callerId` 函數中。 此外，分析工具也可以使用[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_DISABLE_INLINING 值，全域停用內嵌插入。  
  
 插入的函式不會引發輸入或離開的事件。 因此，分析工具必須將 `pfShouldInline` 設定為 `false`，才能產生精確的 callgraph。 將 `pfShouldInline` 設定為 `false` 會影響效能，因為內嵌插入通常會增加速度並減少所插入方法的個別 JIT 編譯事件數。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
