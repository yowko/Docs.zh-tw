---
title: "工作平行程式庫和 PLINQ 中的 ETW 事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工作，ETW 事件"
ms.assetid: 87a9cff5-d86f-4e44-a06e-d12764d0dce2
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# 工作平行程式庫和 PLINQ 中的 ETW 事件
「工作平行程式庫」與 PLINQ 都會產生「Windows 事件追蹤」\(Event Trace for Windows，ETW\) 事件，您可以利用它們，透過使用「Windows 效能分析器」之類的工具，來對應用程式進行程式碼剖析和疑難排解。  然而，在大部分情節中，對平行應用程式程式碼進行程式碼剖析的最佳做法是使用 [!INCLUDE[vsUltShort](../../../includes/vsultshort-md.md)] 中的 [並行視覺化檢視](../Topic/Concurrency%20Visualizer.md)。  
  
## 工作平行程式庫 ETW 事件  
 在 EVENT\_HEADER 結構中，<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName>、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> 和 <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=fullName> 所產生事件的 ProviderId GUID 為：  
  
```  
0x2e5dba47, 0xa3d2, 0x4d16, 0x8e, 0xe0, 0x66, 0x71, 0xff, 0xdc, 0xd7, 0xb5  
```  
  
### 平行迴圈開始  
 EVENT\_DESCRIPTOR.Task \= 1  
  
 EVENT\_DESCRIPTOR.Id \= 1  
  
#### 使用者資料  
  
|**名稱**|**類型**|**說明**|  
|------------|------------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之 TaskScheduler 的 ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之工作的 ID。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|唯一識別項，用來表示具有分叉\/加入語意之事件的巢狀和配對。|  
|OperationType|<xref:System.Int32?displayProperty=fullName>|指出迴圈型別：<br /><br /> 1 \= ParallelInvoke<br /><br /> 2 \= ParallelFor<br /><br /> 3 \= ParallelForEach|  
|InclusiveFrom|<xref:System.Int64?displayProperty=fullName>|迴圈計數器的起始值|  
|ExclusiveTo|<xref:System.Int64?displayProperty=fullName>|迴圈計數器的結束值|  
  
### 平行迴圈結束  
 EVENT\_DESCRIPTOR.Task \= 2  
  
 EVENT\_DESCRIPTOR.Id \= 2  
  
#### 使用者資料  
  
|**名稱**|**類型**|**說明**|  
|------------|------------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之 TaskScheduler 的 ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之工作的 ID。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|唯一識別項，用來表示具有分叉\/加入語意之事件的巢狀和配對。|  
|totalIterations|<xref:System.Int64?displayProperty=fullName>|反覆項目的總數|  
  
### 平行叫用開始  
 EVENT\_DESCRIPTOR.Task \= 3  
  
 EVENT\_DESCRIPTOR.Id \= 3  
  
#### 使用者資料  
  
|**名稱**|**類型**|**說明**|  
|------------|------------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之 TaskScheduler 的 ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之工作的 ID。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|唯一識別項，用來表示具有分叉\/加入語意之事件的巢狀和配對。|  
|totalIterations|<xref:System.Int64?displayProperty=fullName>|反覆項目的總數|  
|operationType|<xref:System.Int32?displayProperty=fullName>|指出迴圈型別：<br /><br /> 1 \= ParallelInvoke<br /><br /> 2 \= ParallelFor<br /><br /> 3 \= ParallelForEach|  
|ActionCount|<xref:System.Int32?displayProperty=fullName>|將在平行叫用中執行的動作數目。|  
  
### 平行叫用結束  
 EVENT\_DESCRIPTOR.Task \= 4  
  
 EVENT\_DESCRIPTOR.Id \= 4  
  
#### 使用者資料  
  
|**名稱**|**類型**|**說明**|  
|------------|------------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之 TaskScheduler 的 ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之工作的 ID。|  
|ForkJoinContextID|<xref:System.Int32?displayProperty=fullName>|唯一識別項，用來表示具有分叉\/加入語意之事件的巢狀和配對。|  
  
## PLINQ ETW 事件  
 PLINQ 的 EVENT\_HEADER.ProviderId GUID 為：  
  
```  
0x159eeeec, 0x4a14, 0x4418, 0xa8, 0xfe, 0xfa, 0xab, 0xcd, 0x98, 0x78, 0x87  
```  
  
### 平行查詢開始  
 EVENT\_DESCRIPTOR.Task \= 1  
  
 EVENT\_DESCRIPTOR.Id \= 1  
  
#### 使用者資料  
  
|**名稱**|**類型**|**說明**|  
|------------|------------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之 TaskScheduler 的 ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之工作的 ID。|  
|QueryID|<xref:System.Int32?displayProperty=fullName>|唯一查詢識別項。|  
  
### 平行查詢結束  
 EVENT\_DESCRIPTOR.Task \= 2  
  
 EVENT\_DESCRIPTOR.Id \= 2  
  
#### 使用者資料  
  
|**名稱**|**類型**|**說明**|  
|------------|------------|------------|  
|OriginatingTaskSchedulerID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之 TaskScheduler 的 ID。|  
|OriginatingTaskID|<xref:System.Int32?displayProperty=fullName>|啟動迴圈之工作的 ID。|  
|QueryID|<xref:System.Int32?displayProperty=fullName>|唯一查詢識別項。|  
  
## 請參閱  
 [.NET Framework 中的 ETW 事件](../../../docs/framework/performance/etw-events.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)