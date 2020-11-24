---
title: ICorProfilerCallback5 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 8e94aebc489fff1c81593e54b17c471e7228d810
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689286"
---
# <a name="icorprofilercallback5-interface"></a>ICorProfilerCallback5 介面

當搭配使用 [ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md) 或 [ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md) 方法搭配 [ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md) 和 [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) 方法時，補充資訊以協助 profiler 識別即時物件的完整關閉。  
  
 `ICorProfilerCallback5` 必須由 Managed 記憶體分析工具實作，以訂閱與相依性控制代碼相關的通知。  
  
## <a name="remarks"></a>備註  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ConditionalWeakTableElementReferences 方法](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|識別那些根目錄透過直接成員欄位參考以及透過 `ConditionalWeakTable` 相依性來參考之物件的可轉移結束。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
