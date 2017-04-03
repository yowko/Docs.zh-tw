---
title: "執行緒共用 (C#) | Microsoft Docs"
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
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
caps.latest.revision: 5
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: da18d75f5d80cd7ad8a9a974bf0ffda196e7ea86
ms.lasthandoff: 03/13/2017

---
# <a name="thread-pooling-c"></a>執行緒共用 (C#)
「執行緒集區」**是可用來在背景執行數項工作的執行緒集合。 (如需背景資訊，請參閱[執行緒處理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md))。這可讓主要執行緒非同步地執行其他工作。  
  
 執行緒集區通常運用於伺服器應用程式中。 每個傳入要求都會指派給執行緒集區中的執行緒，因此可以非同步處理，而不需要輸入主要執行緒或延遲處理後續要求。  
  
 集區中的執行緒完成其工作之後，會回到可在其中重複使用它的等待中執行緒佇列。 這項重複使用可讓應用程式避免建立每個工作之新執行緒的成本。  
  
 執行緒集區一般會有最大數目的執行緒。 如果所有執行緒都忙碌中，則會將其他工作放在佇列中，直到執行緒變成可用時可以服務這些工作為止。  
  
 您可以實作自己的執行緒集區，但透過 <xref:System.Threading.ThreadPool> 類別較容易使用 .NET Framework 所提供的執行緒集區。  
  
 使用執行緒集區，您可以使用您要執行之程序的委派來呼叫 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName> 方法，而 C# 會建立執行緒並執行您的程序。  
  
## <a name="thread-pooling-example"></a>執行緒共用範例  
 下列範例示範如何使用執行緒共用來啟動數個工作。  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 執行緒共用的其中一個優點是您可以將狀態物件中的引數傳遞給工作程序。 如果您要呼叫的程序需要多個引數，則可以將結構或類別執行個體轉換為 `Object` 資料類型。  
  
## <a name="thread-pool-parameters-and-return-values"></a>執行緒集區參數和傳回值  
 從執行緒集區執行緒中傳回值並不直接。 不允許從函式呼叫中傳回值的標準方式，因為 `Sub` 程序是唯一可放入執行緒集區佇列中的程序類型。 其中一種您可以提供參數和傳回值的方式是將參數、傳回值和方法包裝到包裝函式類別，如[多執行緒程序的參數和傳回值 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md) 中所述。  
  
 提供參數和傳回值的較簡單方式是使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法的選擇性 `ByVal` 狀態物件變數。 如果您使用此變數來傳遞類別執行個體的參考，則執行個體的成員可以透過執行緒集區執行緒進行修改，並當作傳回值。  
  
 一開始，可能不明顯，但您可以修改以傳值方式傳遞的變數所參考的物件。 因為物件參考是以傳值方式傳遞，所以您可以執行這項作業。 當您變更物件參考所參考的物件成員時，變更會套用至實際類別執行個體。  
  
 結構無法用來傳回狀態物件內的值。 因為結構是實值型別，所以非同步處理程序所進行的變更不會變更原始結構的成員。 使用結構，以在不需要傳回值時提供參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>   
 <xref:System.Threading>   
 <xref:System.Threading.ThreadPool>   
 [如何：使用執行緒集區 (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)   
 [執行緒處理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)   
 [多執行緒應用程式 (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)   
 [執行緒同步處理 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
