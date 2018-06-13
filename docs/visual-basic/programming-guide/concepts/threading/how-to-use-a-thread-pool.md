---
title: 如何： 使用執行緒集區 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 90a0bb24-39f8-41f5-a217-b52a7d4fed0b
ms.openlocfilehash: a61defc2e40662d7fdadb40693e757fa559adb6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648147"
---
# <a name="how-to-use-a-thread-pool-visual-basic"></a><span data-ttu-id="7dd8a-102">如何： 使用執行緒集區 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dd8a-102">How to: Use a Thread Pool (Visual Basic)</span></span>
<span data-ttu-id="7dd8a-103">「執行緒共用」是一種多執行緒處理，其中的工作會加入佇列，並在建立執行緒時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-103">*Thread pooling* is a form of multithreading in which tasks are added to a queue and automatically started when threads are created.</span></span> <span data-ttu-id="7dd8a-104">如需詳細資訊，請參閱[執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-104">For more information, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md).</span></span>  
  
 <span data-ttu-id="7dd8a-105">下列範例使用 .NET Framework 執行緒集區來計算 20 到 40 之間十個數字的 `Fibonacci` 結果。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-105">The following example uses the .NET Framework thread pool to calculate the `Fibonacci` result for ten numbers between 20 and 40.</span></span> <span data-ttu-id="7dd8a-106">每個 `Fibonacci` 結果都會以 `Fibonacci` 類別表示，該類別提供一個執行計算的方法，稱為 `ThreadPoolCallback`。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-106">Each `Fibonacci` result is represented by the `Fibonacci` class, which provides a method named `ThreadPoolCallback` that performs the calculation.</span></span> <span data-ttu-id="7dd8a-107">這會建立代表每個 `Fibonacci` 值的物件，並將 `ThreadPoolCallback` 方法傳遞至 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>，以指派集區中的可用執行緒來執行此方法。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-107">An object that represents each `Fibonacci` value is created, and the `ThreadPoolCallback` method is passed to <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, which assigns an available thread in the pool to execute the method.</span></span>  
  
 <span data-ttu-id="7dd8a-108">由於會提供半隨機值給每個 `Fibonacci` 物件進行計算，而且每個執行緒會競爭處理器時間，因此您無法事先得知需要多久的時間才能計算完所有十個結果。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-108">Because each `Fibonacci` object is given a semi-random value to compute, and because each thread will be competing for processor time, you cannot know in advance how long it will take for all ten results to be calculated.</span></span> <span data-ttu-id="7dd8a-109">這就是為什麼會在建構期間將每個 `Fibonacci` 物件傳遞至 <xref:System.Threading.ManualResetEvent> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-109">That is why each `Fibonacci` object is passed an instance of the <xref:System.Threading.ManualResetEvent> class during construction.</span></span> <span data-ttu-id="7dd8a-110">每個物件會在計算完成時指出提供的事件物件，這可讓主要執行緒使用 <xref:System.Threading.WaitHandle.WaitAll%2A> 封鎖區塊的執行，直到所有十個 `Fibonacci` 物件都已計算出結果。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-110">Each object signals the provided event object when its calculation is complete, which allows the primary thread to block execution with <xref:System.Threading.WaitHandle.WaitAll%2A> until all ten `Fibonacci` objects have calculated a result.</span></span> <span data-ttu-id="7dd8a-111">`Main` 方法接著會顯示每個 `Fibonacci` 結果。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-111">The `Main` method then displays each `Fibonacci` result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dd8a-112">範例</span><span class="sxs-lookup"><span data-stu-id="7dd8a-112">Example</span></span>  
  
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
  
 <span data-ttu-id="7dd8a-113">以下是輸出的範例。</span><span class="sxs-lookup"><span data-stu-id="7dd8a-113">Following is an example of the output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7dd8a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dd8a-114">See Also</span></span>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="7dd8a-115">執行緒集區 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dd8a-115">Thread Pooling (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="7dd8a-116">執行緒 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dd8a-116">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="7dd8a-117">安全性</span><span class="sxs-lookup"><span data-stu-id="7dd8a-117">Security</span></span>](../../../../standard/security/index.md)
