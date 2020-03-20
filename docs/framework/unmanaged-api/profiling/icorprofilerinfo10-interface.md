---
title: ICorProfilerInfo10 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175066"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 介面

[ICorProfilerInfo9](icorprofilerinfo9-interface.md)的子類，它提供修改函數 IL、查詢運行時資訊以及掛起和恢復運行時的方法。

## <a name="methods"></a>方法  

| 方法|描述|  
| ------------|-----------------|  
|[EnumerateObjectReferences 方法](icorprofilerinfo10-enumerateobjectreferences-method.md)|給定 ObjectID、回檔和用戶端資料，枚舉每個物件引用（如果有）。 |
|[IsFrozenObject 方法](icorprofilerinfo10-isfrozenobject-method.md)|給定 ObjectID，確定物件是否位於唯讀段中。 |
|[GetLOHObjectSizeThreshold 方法](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|獲取配置的 LOH 閾值。 |
|[RequestReJITWithInliners 方法](icorprofilerinfo10-requestrejitwithinliners-method.md)| 重新執行請求的方法，以及所請求方法的任何內襯。  |
|[SuspendRuntime 方法](icorprofilerinfo10-suspendruntime-method.md)| 在不執行 GC 的情況下掛起運行時。 |
|[ResumeRuntime 方法](icorprofilerinfo10-resumeruntime-method.md)| 在不執行 GC 的情況下恢復運行時。 |

## <a name="requirements"></a>需求  
**平臺：** 請參閱[.NET Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。  
**標頭：** CorProf.idl、CorProf.h  
**.NET 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
