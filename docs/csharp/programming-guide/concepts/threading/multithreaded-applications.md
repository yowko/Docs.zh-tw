---
title: "多執行緒應用程式 (C#) | Microsoft Docs"
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
ms.assetid: b7015cfb-d506-4eac-b2f8-b2caaa9cc977
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a36fd71ff41eb219f4c4de36d4fa8da9b8ee179a
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="multithreaded-applications-c"></a>多執行緒應用程式 (C#)
使用 C#，您可以撰寫一次執行多項工作的應用程式。 可能妨礙其他工作的工作可以另外的執行緒執行，此等程序稱之為「多執行緒」**或「無限制執行緒」**。  
  
 使用多執行緒的應用程式回應使用者輸入會更快，因為當處理器密集工作在另外的執行緒上執行時，使用者介面會保持使用中。 當您建立可擴充的應用程式時，多執行緒也很有幫助，因為您可以隨著工作負載增加而新增執行緒。  
  
## <a name="creating-and-using-threads"></a>建立和使用執行緒  
 如果您需要對應用程式執行緒行為有更大的掌控力，您可以自行管理執行緒。 但請了解撰寫正確的多執行緒應用程式十分困難︰您的應用程式可能會停止回應，或因競爭情形造成暫時性錯誤。 如需詳細資訊，請參閱[安全執行緒的元件](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)。  
  
 宣告 <xref:System.Threading.Thread> 型別的變數並呼叫建構函式，提供您要在新執行緒執行的程序或方法名稱，以建立新的執行緒。 下列程式碼提供一個範例。  
  
```csharp  
System.Threading.Thread newThread =  
    new System.Threading.Thread(AMethod);  
```  
  
### <a name="starting-and-stopping-threads"></a>開始和停止執行緒  
 若要開始執行新的執行緒，請使用 <xref:System.Threading.Thread.Start%2A> 方法，如下列程式碼所示。  
  
```csharp  
newThread.Start();  
```  
  
 若要停止執行執行緒，請使用 <xref:System.Threading.Thread.Abort%2A> 方法，如下列程式碼所示。  
  
```csharp  
newThread.Abort();  
```  
  
 除了開始和停止執行緒，您也可以呼叫 <xref:System.Threading.Thread.Sleep%2A> 或 <xref:System.Threading.Thread.Suspend%2A> 方法暫停執行緒，使用 <xref:System.Threading.Thread.Resume%2A> 方法恢復暫停的執行緒，以及使用 <xref:System.Threading.Thread.Abort%2A> 方法終結執行緒。  
  
### <a name="thread-methods"></a>執行緒方法  
 下表顯示可用來控制個別執行緒的一些方法。  
  
|方法|動作|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|讓執行緒開始執行。|  
|<xref:System.Threading.Thread.Sleep%2A>|讓執行緒暫停指定的時間。|  
|<xref:System.Threading.Thread.Suspend%2A>|當執行緒到達安全點時暫停。|  
|<xref:System.Threading.Thread.Abort%2A>|當執行緒到達安全點時停止。|  
|<xref:System.Threading.Thread.Resume%2A>|重新開始暫止的執行緒|  
|<xref:System.Threading.Thread.Join%2A>|讓目前的執行緒等候另一個執行緒完成。 如果搭配逾時值使用，當執行緒於配置時間內完成時，此方法會傳回 `True`。|  
  
### <a name="safe-points"></a>安全點  
 這些方法大多都一目了然，但您可能不熟悉「安全點」**的概念。 安全點是程式碼中，通用語言執行平台執行自動「記憶體回收」**的安全位置，記憶體回收是釋放未使用的變數並回收記憶體的程序。 當您呼叫執行緒的 <xref:System.Threading.Thread.Abort%2A> 或 <xref:System.Threading.Thread.Suspend%2A> 方法時，通用語言執行平台會分析程式碼，並決定適當的位置供執行緒停止執行。  
  
### <a name="thread-properties"></a>執行緒屬性  
 執行緒也包含多個有用的屬性，如下表所示︰  
  
|屬性|值|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|如果執行緒在使用中，即包含值 `True`。|  
|<xref:System.Threading.Thread.IsBackground%2A>|取得或設定布林值，指出執行緒是否為或應該是背景執行緒。 背景執行緒類似前景執行緒，但是背景執行緒不會防止處理程序停止。 一旦屬於處理程序的所有前景執行緒停止，通用語言執行平台會呼叫背景執行緒上仍在執行的 <xref:System.Threading.Thread.Abort%2A> 方法結束處理程序。|  
|<xref:System.Threading.Thread.Name%2A>|取得或設定執行緒名稱。 最常用於在偵錯時探索個別執行緒。|  
|<xref:System.Threading.Thread.Priority%2A>|取得或設定作業系統使用的值，以設定執行緒排程的優先權。|  
|<xref:System.Threading.Thread.ThreadState%2A>|包含說明執行緒狀態的值。|  
  
## <a name="thread-priorities"></a>執行緒優先順序  
 每個執行緒都有優先順序屬性，決定它必須執行多大或多小的處理器時段。 作業系統會配置較長的時段給高優先順序的執行緒，較短的時間配量給低優先順序的執行緒。 新執行緒使用 `Normal` 值建立，但是您可以將 <xref:System.Threading.Thread.Priority%2A> 屬性變更成 <xref:System.Threading.ThreadPriority> 列舉中的任一值。  
  
 如需各種執行緒優先順序的詳細說明，請參閱 <xref:System.Threading.ThreadPriority>。  
  
## <a name="foreground-and-background-threads"></a>前景和背景執行緒  
 「前景執行緒」**無限期執行，而「背景執行緒」**會在最後一個前景執行緒停止後立刻停止。 您可以使用 <xref:System.Threading.Thread.IsBackground%2A> 屬性來判斷或變更執行緒的背景狀態。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread>   
 [執行緒同步處理 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)   
 [多執行緒程序的參數和傳回值 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)   
 [執行緒處理 (C++)](../../../../csharp/programming-guide/concepts/threading/index.md)
