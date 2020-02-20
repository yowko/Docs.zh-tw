---
title: ICorProfilerInfo10 介面
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 30179c7c198a343baa3fa01ae64f6d580a3f9e7e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452197"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 介面

[ICorProfilerInfo9](icorprofilerinfo9-interface.md)的子類別，提供修改函式 IL 的方法、從執行時間查詢資訊，以及暫停和繼續執行時間。

## <a name="methods"></a>方法  

| 方法|描述|  
| ------------|-----------------|  
|[EnumerateObjectReferences 方法](icorprofilerinfo10-enumerateobjectreferences-method.md)|假設有 ObjectID、callback 和 clientData，會列舉每個物件參考（如果有的話）。 |
|[IsFrozenObject 方法](icorprofilerinfo10-isfrozenobject-method.md)|給定 ObjectID，判斷物件是否在唯讀區段中。 |
|[GetLOHObjectSizeThreshold 方法](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|取得設定的 LOH 臨界值。 |
|[RequestReJITWithInliners 方法](icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs 要求的方法，以及所要求之方法的任何 inliners。  |
|[SuspendRuntime 方法](icorprofilerinfo10-suspendruntime-method.md)| 暫停執行時間，而不執行 GC。 |
|[ResumeRuntime 方法](icorprofilerinfo10-resumeruntime-method.md)| 繼續執行時間，而不執行 GC。 |

## <a name="requirements"></a>需求  
**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?pivots=os-windows)。  
**標頭：** CorProf.idl、CorProf.h  
**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
