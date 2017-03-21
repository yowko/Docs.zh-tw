---
title: "如何︰ 使用執行緒集區 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 90a0bb24-39f8-41f5-a217-b52a7d4fed0b
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d60bceea0ed956075233f5f045131ffb2eb37eef
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-a-thread-pool-visual-basic"></a>如何︰ 使用執行緒集區 (Visual Basic)
*執行緒集區*是一種多執行緒處理哪些工作加入佇列，而且系統會建立執行緒時自動啟動。 如需詳細資訊，請參閱[執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)。  
  
 下列範例會使用.NET Framework 執行緒集區來計算`Fibonacci`20 到 40 之間的 10 個數字的結果。 每個`Fibonacci`結果由`Fibonacci`類別，可提供方法，名為`ThreadPoolCallback`來執行計算。 物件，表示每個`Fibonacci`值的建立，而`ThreadPoolCallback`方法傳遞至<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>，這會指派可用的執行緒集區來執行方法中。</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
  
 因為每個`Fibonacci`物件提供了半隨機值來計算，而且每個執行緒都會競爭處理器時間，因為無法知道事先花多少時間將會計算所有的十個結果。 這就是為什麼每個`Fibonacci`物件的執行個體傳遞<xref:System.Threading.ManualResetEvent>類別在建構期間。</xref:System.Threading.ManualResetEvent> 每個物件表示提供的事件物件計算完成時，可讓主執行緒使用的區塊執行<xref:System.Threading.WaitHandle.WaitAll%2A>直到全部十`Fibonacci`物件已經計算的結果。</xref:System.Threading.WaitHandle.WaitAll%2A> `Main`方法接著會顯示每個`Fibonacci`結果。  
  
## <a name="example"></a>範例  
  
```vb  
Imports System.Threading  
  
Module Module1  
  
    Public Class Fibonacci  
        Private _n As Integer  
        Private _fibOfN  
        Private _doneEvent As ManualResetEvent  
  
        Public ReadOnly Property N() As Integer  
            Get  
                Return _n  
            End Get  
        End Property  
  
        Public ReadOnly Property FibOfN() As Integer  
            Get  
                Return _fibOfN  
            End Get  
        End Property  
  
        Sub New(ByVal n As Integer, ByVal doneEvent As ManualResetEvent)  
            _n = n  
            _doneEvent = doneEvent  
        End Sub  
  
        ' Wrapper method for use with the thread pool.  
        Public Sub ThreadPoolCallBack(ByVal threadContext As Object)  
            Dim threadIndex As Integer = CType(threadContext, Integer)  
            Console.WriteLine("thread {0} started...", threadIndex)  
            _fibOfN = Calculate(_n)  
            Console.WriteLine("thread {0} result calculated...", threadIndex)  
            _doneEvent.Set()  
        End Sub  
  
        Public Function Calculate(ByVal n As Integer) As Integer  
            If n <= 1 Then  
                Return n  
            End If  
            Return Calculate(n - 1) + Calculate(n - 2)  
        End Function  
  
    End Class  
  
    <MTAThread()>   
    Sub Main()  
        Const FibonacciCalculations As Integer = 9 ' 0 to 9  
  
        ' One event is used for each Fibonacci object  
        Dim doneEvents(FibonacciCalculations) As ManualResetEvent  
        Dim fibArray(FibonacciCalculations) As Fibonacci  
        Dim r As New Random()  
  
        ' Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations)  
  
        For i As Integer = 0 To FibonacciCalculations  
            doneEvents(i) = New ManualResetEvent(False)  
            Dim f = New Fibonacci(r.Next(20, 40), doneEvents(i))  
            fibArray(i) = f  
            ThreadPool.QueueUserWorkItem(AddressOf f.ThreadPoolCallBack, i)  
        Next  
  
        ' Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents)  
        Console.WriteLine("All calculations are complete.")  
  
        ' Display the results.  
        For i As Integer = 0 To FibonacciCalculations  
            Dim f As Fibonacci = fibArray(i)  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN)  
        Next  
    End Sub  
  
End Module  
```  
  
 以下是輸出的範例。  
  
```  
launching 10 tasks...  
thread 0 started...  
thread 1 started...  
thread 1 result calculated...  
thread 2 started...  
thread 2 result calculated...  
thread 3 started...  
thread 3 result calculated...  
thread 4 started...  
thread 0 result calculated...  
thread 5 started...  
thread 5 result calculated...  
thread 6 started...  
thread 4 result calculated...  
thread 7 started...  
thread 6 result calculated...  
thread 8 started...  
thread 8 result calculated...  
thread 9 started...  
thread 9 result calculated...  
thread 7 result calculated...  
All calculations are complete.  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(25) = 75025  
Fibonacci(22) = 17711  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(29) = 514229  
Fibonacci(38) = 39088169  
Fibonacci(21) = 10946  
Fibonacci(27) = 196418  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Mutex></xref:System.Threading.Mutex>   
 <xref:System.Threading.WaitHandle.WaitAll%2A></xref:System.Threading.WaitHandle.WaitAll%2A>   
 <xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.EventWaitHandle.Set%2A></xref:System.Threading.EventWaitHandle.Set%2A>   
 <xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool>   
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>   
 <xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent>   
 [執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)   
 [執行緒處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 @System.Threading.Monitor   
 [安全性](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6)
