---
title: ICorProfilerCallback::ClassUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 5d9474f78dd8b999a37f60e0698cfd04240b897a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866568"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a>ICorProfilerCallback::ClassUnloadFinished 方法
通知分析工具，類別已完成卸載。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>參數

- `classId`

  中的 \[] 可識別已卸載的類別。

- `hrStatus`

  \[in]） HRESULT，指出是否已成功卸載類別。
  
## <a name="remarks"></a>備註  
 卸載類別的某些部分可能會在 `ClassUnloadFinished` 回呼之後繼續進行。 `hrStatus` 中的失敗 HRESULT 表示失敗。 不過，`hrStatus` 中的成功 HRESULT 只會指出卸載類別的第一個部分已成功。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ClassUnloadStarted 方法](icorprofilercallback-classunloadstarted-method.md)
