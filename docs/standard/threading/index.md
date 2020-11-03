---
title: Managed 執行緒處理
description: 請參閱 .NET 中 managed 執行緒的連結，其中涵蓋了基本概念、最佳作法、執行緒物件 & 功能、參考頁面 & 更多專案。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: 15af6268c8e5de853ead0817c85f4261c7fc9692
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189169"
---
# <a name="managed-threading"></a>受控執行緒

無論您是針對具有一個或多個處理器的電腦進行開發，您都想要讓應用程式能夠提供與使用者的最快速回應，即使應用程式目前正在執行其他工作也是一樣。 使用多執行緒的執行是一種讓應用程式能迅速回應使用者，同時能夠在使用者事件之間或甚至在使用者事件當中善用處理器的強大方法。 雖然本節將介紹執行緒處理的基本概念，但是重點會放在 Managed 執行緒處理概念和如何使用 Managed 執行緒處理。  
  
> [!NOTE]
> 從 .NET Framework 4 開始，多執行緒程式設計已透過 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 和類別大幅簡化 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 、 [平行 LINQ (PLINQ) ](../parallel-programming/introduction-to-plinq.md)、命名空間中的並行集合類別 <xref:System.Collections.Concurrent?displayProperty=nameWithType> ，以及以工作（而非執行緒）概念為基礎的程式設計模型。 如需詳細資訊，請參閱 [平行程式設計](../parallel-programming/index.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [Managed 執行緒處理的基本概念](managed-threading-basics.md)  
 提供 Managed 執行緒處理的概觀，並討論何時使用多個執行緒。  
  
 [使用執行緒和執行緒](using-threads-and-threading.md)  
 說明如何建立、啟動、暫停、繼續和中止執行緒。  
  
 [Managed 執行緒處理的最佳實施方針](managed-threading-best-practices.md)  
 討論同步處理的層級、如何避免死結和競爭條件，以及其他執行緒處理問題。  
  
 [執行緒物件和功能](threading-objects-and-features.md)  
 描述可用來同步執行緒活動的 Managed 類別，以及在不同執行緒上存取的物件資料，並提供執行緒集區執行緒的概觀。  
  
## <a name="reference"></a>參考  
 <xref:System.Threading>  
 包含使用和同步 Managed 執行緒的類別。  
  
 <xref:System.Collections.Concurrent>  
 包含可安全用於多個執行緒的集合類別。  
  
 <xref:System.Threading.Tasks>  
 包含建立和排程並行處理工作的類別。  
  
## <a name="related-sections"></a>相關章節  
 [應用程式定義域](../../framework/app-domains/application-domains.md)  
 提供應用程式定義域的概觀及通用語言基礎結構如何使用它們。  
  
 [非同步檔案 i/o](../io/asynchronous-file-i-o.md)  
 描述非同步 I/O 的效能利益和基本作業。  
  
 [以工作為基礎的非同步模式 (TAP)](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 提供 .NET 中非同步程式設計建議模式的概觀。  
  
 [以非同步的方式呼叫同步方法](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 說明如何使用內建的委派功能在執行緒集區執行緒上呼叫方法。  
  
 [平行程式設計](../parallel-programming/index.md)  
 描述平行程式設計程式庫，簡化應用程式中多個執行緒的用法。  
  
 [平行 LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md)  
 描述以平行方式執行查詢的系統，以善用多個處理器。
