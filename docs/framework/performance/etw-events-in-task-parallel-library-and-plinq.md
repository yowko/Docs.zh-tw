---
title: 工作平行程式庫和 PLINQ 中的 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, ETW events
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c5b372073b00f30312a83ae88ae0dbb6885d1a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="etw-events-in-task-parallel-library-and-plinq"></a>工作平行程式庫和 PLINQ 中的 ETW 事件
工作平行程式庫和 PLINQ 都會產生 Windows 事件追蹤 (ETW) 事件，您可使用 Windows Performance Analyzer 等工具，利用這些事件對應用程式進行程式碼剖析和疑難排解。 然而，在大部分情節中，對平行應用程式程式碼進行程式碼剖析的最佳做法是使用 [!INCLUDE[vsUltShort](../../../includes/vsultshort-md.md)] 中的[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。  
  
## <a name="task-parallel-library-etw-events"></a>工作平行程式庫 ETW 事件  
 在 EVENT_HEADER 結構中，<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType> 產生的事件 ProviderId GUID 是：  
  
```  
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5  
```  
  
### <a name="parallel-loop-begin"></a>平行迴圈開始  
 EVENT_DESCRIPTOR.Task = 1  
  
 EVENT_DESCRIPTOR.Id = 1  
  
#### <a name="user-data"></a>使用者資料  
  
|**名稱**|**Type**|**描述**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的 TaskScheduler 識別碼。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的工作識別碼。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|用來指出巢狀結構和事件派生/聯結語意組的唯一識別碼。|  
|OperationType|<xref:System.Int32?displayProperty=nameWithType>|指出迴圈的類型：<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|  
|InclusiveFrom|<xref:System.Int64?displayProperty=nameWithType>|迴圈計數器的起始值|  
|ExclusiveTo|<xref:System.Int64?displayProperty=nameWithType>|迴圈計數器的結束值|  
  
### <a name="parallel-loop-end"></a>平行迴圈結束  
 EVENT_DESCRIPTOR.Task = 2  
  
 EVENT_DESCRIPTOR.Id = 2  
  
#### <a name="user-data"></a>使用者資料  
  
|**名稱**|**Type**|**描述**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的 TaskScheduler 識別碼。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的工作識別碼。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|用來指出巢狀結構和事件派生/聯結語意組的唯一識別碼。|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|反覆項目總數|  
  
### <a name="parallel-invoke-begin"></a>平行叫用開始  
 EVENT_DESCRIPTOR.Task = 3  
  
 EVENT_DESCRIPTOR.Id = 3  
  
#### <a name="user-data"></a>使用者資料  
  
|**名稱**|**Type**|**描述**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的 TaskScheduler 識別碼。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的工作識別碼。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|用來指出巢狀結構和事件派生/聯結語意組的唯一識別碼。|  
|totalIterations|<xref:System.Int64?displayProperty=nameWithType>|反覆項目總數|  
|operationType|<xref:System.Int32?displayProperty=nameWithType>|指出迴圈的類型：<br /><br /> 1 = ParallelInvoke<br /><br /> 2 = ParallelFor<br /><br /> 3 = ParallelForEach|  
|ActionCount|<xref:System.Int32?displayProperty=nameWithType>|在平行叫用中會執行的動作數目。|  
  
### <a name="parallel-invoke-end"></a>平行叫用結束  
 EVENT_DESCRIPTOR.Task = 4  
  
 EVENT_DESCRIPTOR.Id = 4  
  
#### <a name="user-data"></a>使用者資料  
  
|**名稱**|**Type**|**描述**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的 TaskScheduler 識別碼。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的工作識別碼。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=nameWithType>|用來指出巢狀結構和事件派生/聯結語意組的唯一識別碼。|  
  
## <a name="plinq-etw-events"></a>PLINQ ETW 事件  
 PLINQ 的 EVENT_HEADER.ProviderId GUID 是：  
  
```  
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87  
```  
  
### <a name="parallel-query-begin"></a>平行查詢開始  
 EVENT_DESCRIPTOR.Task = 1  
  
 EVENT_DESCRIPTOR.Id = 1  
  
#### <a name="user-data"></a>使用者資料  
  
|**名稱**|**Type**|**描述**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的 TaskScheduler 識別碼。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的工作識別碼。|  
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|唯一的查詢識別碼。|  
  
### <a name="parallel-query-end"></a>平行查詢結束  
 EVENT_DESCRIPTOR.Task = 2  
  
 EVENT_DESCRIPTOR.Id = 2  
  
#### <a name="user-data"></a>使用者資料  
  
|**名稱**|**Type**|**描述**|  
|--------------|--------------|---------------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的 TaskScheduler 識別碼。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=nameWithType>|啟動迴圈的工作識別碼。|  
|QueryID|<xref:System.Int32?displayProperty=nameWithType>|唯一的查詢識別碼。|  
  
## <a name="see-also"></a>另請參閱  
 [.NET Framework 中的 ETW 事件](../../../docs/framework/performance/etw-events.md)  
 [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [平行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
