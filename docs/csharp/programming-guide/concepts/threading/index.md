---
title: "執行緒處理 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: e3f213b43c2f05a5afef1db7aec8b9c2695df989
ms.contentlocale: zh-tw
ms.lasthandoff: 06/12/2017

---
# <a name="threading-c"></a>執行緒處理 (C#)
執行緒處理，可讓 C# 程式執行並行處理，因此您可以執行多個作業一次。 例如，您可以使用執行緒來監視使用者的輸入、 執行背景工作，以及處理同時的輸入資料流。  
  
 執行緒具有下列屬性：  
  
-   執行緒可讓程式執行並行處理。  
  
-   .NET Framework<xref:System.Threading>命名空間會使得使用執行緒更容易。  
  
-   執行緒共用應用程式的資源。 如需詳細資訊，請參閱[使用執行緒和執行緒處理](https://msdn.microsoft.com/library/e1dx6b2h)。  
  
 根據預設，C# 程式都有一個執行緒。 不過，可以建立及使用主執行緒和平行執行程式碼輔助執行緒。 這些執行緒通常稱為*背景工作執行緒*。  
  
 背景工作執行緒可用來執行耗費時間或時間緊急工作，而主要執行緒所佔用。 比方說，背景工作執行緒通常使用於伺服器應用程式不需等到完成前一個要求符合連入要求。 背景工作執行緒也可用來執行桌面應用程式中的 「 背景 」 工作，讓主執行緒的磁碟機的使用者介面項目-仍能繼續回應使用者動作。  
  
 執行緒處理以解決問題的輸送量和回應性，但它也可能導致資源共用的問題，例如死結和競爭情形。 多個執行緒最適合需要不同的資源，例如檔案控制代碼和網路連線的工作。 指派給單一資源的多個執行緒可能會造成同步處理問題，而需要經常封鎖其他執行緒等候時就失去了使用多個執行緒的目的。  
  
 常用的策略是使用背景工作執行緒執行耗費時間很重要的工作不需要許多其他的執行緒所使用的資源。 當然，您的程式中的某些資源必須由多個執行緒存取。 這些情況下，<xref:System.Threading>命名空間提供類別同步處理執行緒。 這些類別包括<xref:System.Threading.Mutex>， <xref:System.Threading.Monitor>， <xref:System.Threading.Interlocked>， <xref:System.Threading.AutoResetEvent>，和<xref:System.Threading.ManualResetEvent>。  
  
 您可以使用部分或所有這些類別來同步處理活動的多個執行緒，但某些執行緒支援 C# 語言。 例如， [Lock 陳述式](../../../../csharp/language-reference/keywords/lock-statement.md)提供同步處理功能，透過使用隱含<xref:System.Threading.Monitor>。  
  
> [!NOTE]
>  開頭[!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)]，多執行緒的程式設計簡化了<xref:System.Threading.Tasks.Parallel?displayProperty=fullName>和<xref:System.Threading.Tasks.Task?displayProperty=fullName>類別，[平行 LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688)，新的並行集合中的類別<xref:System.Collections.Concurrent?displayProperty=fullName>命名空間，以及新的程式設計模型為基礎的工作，而不是執行緒概念。 如需詳細資訊，請參閱[平行程式設計](https://msdn.microsoft.com/library/dd460693)。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[多執行緒應用程式 (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|描述如何建立及使用執行緒。|  
|[參數和傳回值的多執行緒程序 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|描述如何傳遞和傳回參數的多執行緒應用程式。|  
|[逐步解說： 使用 BackgroundWorker 元件 (C#) 進行多執行緒處理](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|示範如何建立簡單的多執行緒應用程式。|  
|[執行緒同步處理 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|描述如何控制執行緒的互動。|  
|[執行緒計時器 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|描述如何在固定時間間隔的個別執行緒上執行程序。|  
|[執行緒集區 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|描述如何使用系統所管理的背景工作執行緒集區。|  
|[如何： 使用執行緒集區 (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|示範如何同步處理的執行緒集區中的多個執行緒使用。|  
|[執行緒處理](https://msdn.microsoft.com/library/3e8s7xdd)|描述如何實作.NET Framework 中的執行緒。|
