---
title: ICorProfilerCallback::FunctionUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 2b228337a55d50b94da966b45877e2000b3c03e4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866308"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a>ICorProfilerCallback::FunctionUnloadStarted 方法
通知分析工具，執行時間已開始卸載函數。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a>參數

- `functionId`

  \[in] 所卸載之函式的識別碼。

## <a name="remarks"></a>備註  
 這個方法傳回給呼叫端之後，`functionId` 參數的值已不再有效。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
