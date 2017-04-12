---
title: "執行緒集區 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6037d7ea17e260d44bae571aa25d413996f5a123
ms.lasthandoff: 03/13/2017

---
# <a name="thread-pooling-visual-basic"></a>執行緒集區 (Visual Basic)
A*執行緒集區*是可用來在背景中執行幾項工作的執行緒的集合。 (請參閱[執行緒 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)背景資訊。)這會使主要執行緒可以執行其他工作以非同步的方式。  
  
 執行緒集區通常會運用在伺服器應用程式。 每個傳入要求被指派給一個執行緒在執行緒集區，以便可以以非同步方式處理要求，而不用中斷主要執行緒或延遲處理的後續要求。  
  
 當執行緒集區中的完成其工作時，它會回到佇列等待執行緒可重複使用。 這種重新使用可讓應用程式，以避免建立新的執行緒，每個工作的成本。  
  
 執行緒集區通常會有最大執行緒數目。 所有執行緒都都在忙碌中，如果其他工作都被放在佇列中，直到執行緒可提供服務。  
  
 您可以實作自己的執行緒集區，但很容易使用透過<xref:System.Threading.ThreadPool>類別</xref:System.Threading.ThreadPool>的.NET Framework 所提供的執行緒集區  
  
 執行緒集區，您就呼叫<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>想要執行的程序的方法的委派和 Visual Basic 建立的執行緒，並執行您的程序。</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>  
  
## <a name="thread-pooling-example"></a>執行緒集區範例  
 下列範例顯示如何使用執行緒集區啟動數個工作。  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 執行緒集區的其中一個優點是，您可以傳遞的狀態物件的引數給工作的程序。 如果您要呼叫的程序需要多個引數，則可以轉換的結構或到類別的執行個體`Object`資料型別。  
  
## <a name="thread-pool-parameters-and-return-values"></a>執行緒集區參數和傳回值  
 傳回值，從執行緒集區執行緒並不簡單。 不允許從函式呼叫傳回值的標準方式，因為`Sub`程序是唯一可以排入執行緒集區的程序的類型。 其中一種您可以提供參數，並傳回值是藉由包裝參數，傳回的值與包裝函式中的方法類別中所述[參數和傳回值的多執行緒程序 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)。  
  
 提供的參數和傳回值解碼方法是使用選擇性`ByVal`狀態的物件變數<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>方法。</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 如果您使用此變數傳遞類別的執行個體的參考時，可以修改執行緒集區執行緒之執行個體成員，並當做傳回值。  
  
 一開始它可能不明顯，您可以修改傳值方式傳遞變數所參考的物件。 您可以執行這項操作，因為物件參考傳值方式傳遞。 當您變更成員的物件參考所參考的物件時，所做的變更會套用至實際的類別執行個體。  
  
 結構無法用於傳回狀態物件內的值。 由於結構是實值型別，對這個非同步處理序的變更，就不會變更原始結構的成員。 使用提供的參數，不需要傳回值時的結構。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>   
 <xref:System.Threading></xref:System.Threading>   
 <xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool>   
 [如何︰ 使用執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)   
 [執行緒處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 [多執行緒應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [執行緒同步處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
