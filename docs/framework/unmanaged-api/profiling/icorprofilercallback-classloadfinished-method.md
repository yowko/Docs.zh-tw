---
title: ICorProfilerCallback::ClassLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: 4be2a50664b001e865b5ecdd9aabe8ba727b8c26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500386"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a>ICorProfilerCallback::ClassLoadFinished 方法
通知 profiler，類別已完成載入。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>參數

- `classId`

  \[在中，識別已載入的類別。

- `hrStatus`

  \[in] 中的 HRESULT，指出類別是否已成功載入。

## <a name="remarks"></a>備註  
 在 `classId` 呼叫方法之前，的值對資訊要求而言是不正確 `ClassLoadFinished` 。  
  
 載入類別的某些部分可能會在回呼之後繼續進行 `ClassLoadFinished` 。 中的失敗 HRESULT `hrStatus` 表示失敗。 不過，中的成功 HRESULT `hrStatus` 只會指出載入類別的第一個部分已成功。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ClassLoadStarted 方法](icorprofilercallback-classloadstarted-method.md)
