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
ms.openlocfilehash: 13ce44c9c7a04b870278bc8926dd9fe5daf10bc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500009"
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
 在將在其中插入函式的函式識別碼 `calleeId` 。  
  
 `calleeId`  
 在要插入之函式的識別碼。  
  
 `pfShouldInline`  
 [out] `true`表示允許進行插入;否則為 `false` 。  
  
## <a name="remarks"></a>備註  
 分析工具可以將設定 `pfShouldInline` 為 `false` ，以防止函式插入函式 `calleeId` 中 `callerId` 。 此外，分析工具也可以使用[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_DISABLE_INLINING 值，全域停用內嵌插入。  
  
 插入的函式不會引發輸入或離開的事件。 因此，分析工具必須將設為，才能 `pfShouldInline` `false` 產生精確的 callgraph。 將設定 `pfShouldInline` 為 `false` 會影響效能，因為內嵌插入通常會增加速度，並減少所插入方法的個別 JIT 編譯事件數目。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
