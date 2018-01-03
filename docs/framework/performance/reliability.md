---
title: "可靠性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3329bff14d2ab395fecfde0f26942b7cb1b9640e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="reliability"></a>可靠性
重要的是，在 SQL Server 這類伺服器環境中執行的程式碼可防止發生非同步例外狀況。 如這裡所討論，可靠性不是 SQL Server 特有的，而是針對任何在 .NET Framework 2.0 版環境中執行的主機撰寫可靠程式碼。 不過，SQL Server 是大規模使用 2.0 版新可靠性功能的第一個服務，因此當成範例使用。  
  
 在 SQL Server 中執行的程式碼必須處理比其他伺服器環境更嚴格的可靠性方針。 這是因為 SQL Server 的穩定作業處於資源耗用邊緣。  在 SQL Server 環境中，<xref:System.OutOfMemoryException> 和 <xref:System.Threading.ThreadAbortException> 例外狀況並不常見。 這些方針一般較不著重可靠性，但較著重允許完全受信任的 Managed 程式碼在面對 <xref:System.AppDomain> 層級回收時依正常程序失敗，而這是伺服器維護一致性和可用性的主要方式。  
  
## <a name="in-this-section"></a>本節內容  
 [SQL Server 程式設計和主機保護屬性](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)  
 描述 SQL Server 如何使用 <xref:System.Security.Permissions.HostProtectionAttribute> 屬性來限制 Managed 程式碼的執行。  
  
 [可靠性最佳做法](../../../docs/framework/performance/reliability-best-practices.md)  
 提供撰寫符合可靠性需求之程式碼的方針。  
  
 [限制的執行區域](../../../docs/framework/performance/constrained-execution-regions.md)  
 描述限制的執行區域 (CER) 的功能和行為。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
