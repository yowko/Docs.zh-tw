---
title: "可靠性 | Microsoft Docs"
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
  - "程式碼, 可靠性"
  - "Managed 程式碼, 可靠性"
  - "可靠性 [.NET Framework]"
  - "SQL Server [.NET Framework]"
  - "編寫可靠的程式碼"
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# 可靠性
在類似 SQL Server 的伺服器環境中執行的程式碼要防止非同步例外狀況的發生，這一點相當重要。  這裡所討論的可靠性並不是 SQL Server 所特有，而是要針對在 .NET Framework 2.0 版環境下執行的任何主應用程式編寫可靠的程式碼。  但是，SQL Server 是第一個大規模使用 2.0 版的新可靠性功能的服務，所以在這裡將它當成範例使用。  
  
 在 SQL Server 中執行的程式碼所處理的可靠性方針，要比其他伺服器環境更為嚴格。  這是因為 SQL Server 的穩定作業在資源耗用的邊緣。 <xref:System.OutOfMemoryException> 和 <xref:System.Threading.ThreadAbortException> 例外狀況不常見於 SQL Server 環境。  這些方針通常比較少著重在可靠性，而比較多著重在讓完全信任的 Managed 程式碼可以在面臨 <xref:System.AppDomain> 層級的回收時正常地失敗，這是伺服器維護一致性和可用性的主要方法。  
  
## 在本節中  
 [SQL Server 程式設計和主機保護屬性](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 描述 SQL Server 要如何使用 <xref:System.Security.Permissions.HostProtectionAttribute> 屬性來限制 Managed 程式碼的執行。  
  
 [可靠性最佳作法](../../../docs/framework/performance/reliability-best-practices.md)  
 提供編寫符合可靠性要求之程式碼所遵循的方針。  
  
 [限制的執行區域](../../../docs/framework/performance/constrained-execution-regions.md)  
 描述限制的執行區域 \(CER\) 之功能和行為。  
  
## 參考  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>