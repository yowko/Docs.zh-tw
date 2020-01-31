---
title: ICorProfilerCallback3::InitializeForAttach 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: d0219751987b1f2d78ee37a1553b323014c1ccfe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865684"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>ICorProfilerCallback3::InitializeForAttach 方法
由 Common Language Runtime (CLR) 呼叫，讓分析工具在附加作業之後有機會初始化其狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a>參數  
 `pCorProfilerInfoUnk`  
 [in] `ICorProfilerInfo*` 介面的介面指標。  
  
 `pvClientData`  
 在在其 `pvClientData` 參數中傳遞至[IClrProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)方法之資料的指標。 如果這個參數為 null，則 `cbClientData` 將會是 0 (零)。 從 `InitializeForAttach` 傳回時，CLR 會釋放這個記憶體。  
  
 `cbClientData`  
 [in] `pvClientData` 指向的資料大小 (以位元組為單位)。  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫 `InitializeForAttach`，讓分析工具有機會要求回呼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
