---
title: "參數和傳回值的多執行緒程序 (Visual Basic) |Microsoft 文件"
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
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6d1eb53454b6e0d964be15df2e320ce189e7d875
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a><span data-ttu-id="f2e02-102">參數和傳回值的多執行緒程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2e02-102">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>
<span data-ttu-id="f2e02-103">提供和傳回值的多執行緒應用程式中很複雜，因為執行緒類別的建構函式必須傳遞到採用任何引數，且不傳回值的程序的參考。</span><span class="sxs-lookup"><span data-stu-id="f2e02-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="f2e02-104">下列各節說明一些簡單的方法來提供參數，以及從程序傳回值，在個別執行緒上。</span><span class="sxs-lookup"><span data-stu-id="f2e02-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="f2e02-105">如需多執行緒程序中提供的參數</span><span class="sxs-lookup"><span data-stu-id="f2e02-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="f2e02-106">提供多執行緒的方法呼叫參數的最佳方式是將目標方法包裝在類別中，並將做為參數的新執行緒的類別定義欄位。</span><span class="sxs-lookup"><span data-stu-id="f2e02-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="f2e02-107">這種方法的優點是，您可以建立類別的新執行個體使用它自己的參數，每次您想要啟動新執行緒。</span><span class="sxs-lookup"><span data-stu-id="f2e02-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="f2e02-108">例如，假設您有函式會計算區域中的三角形，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="f2e02-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 <span data-ttu-id="f2e02-109">您可以撰寫類別包裝`CalcArea`函式並建立欄位來儲存輸入的參數，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="f2e02-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="f2e02-110">若要使用`AreaClass`，您可以建立`AreaClass`物件，然後設定`Base`和`Height`屬性，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="f2e02-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 <span data-ttu-id="f2e02-111">請注意，`TestArea`程序不會檢查值`Area`欄位之後呼叫`CalcArea`方法。</span><span class="sxs-lookup"><span data-stu-id="f2e02-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="f2e02-112">因為`CalcArea`個別的執行緒上執行`Area`欄位不保證只有當您呼叫之後立即檢查設定`Thread.Start`。</span><span class="sxs-lookup"><span data-stu-id="f2e02-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="f2e02-113">下一節中討論更好的方法，從多執行緒程序傳回值。</span><span class="sxs-lookup"><span data-stu-id="f2e02-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="f2e02-114">從多執行緒程序傳回值</span><span class="sxs-lookup"><span data-stu-id="f2e02-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="f2e02-115">從個別執行緒執行的程序傳回值複雜的程序不可為函式，且無法使用`ByRef`引數。</span><span class="sxs-lookup"><span data-stu-id="f2e02-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="f2e02-116">傳回值的最簡單方式是使用<xref:System.ComponentModel.BackgroundWorker>元件來管理您的執行緒，並引發事件的工作完成時，並處理與事件處理常式的結果。</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="f2e02-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="f2e02-117">下列範例會傳回值，藉由引發另一個執行緒上執行的程序中的事件︰</span><span class="sxs-lookup"><span data-stu-id="f2e02-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 <span data-ttu-id="f2e02-118">您可以提供參數，並使用選擇性的數值傳回執行緒集區執行緒`ByVal`狀態物件變數<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>方法。</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="f2e02-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="f2e02-119">執行緒計時器執行緒也支援狀態物件，針對此目的。</span><span class="sxs-lookup"><span data-stu-id="f2e02-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="f2e02-120">如需執行緒集區和執行緒計時器，請參閱[執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[執行緒集區](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701)和[執行緒計時器 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e02-120">For information on thread pooling and thread timers, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) and [Thread Timers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2e02-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2e02-121">See Also</span></span>  
 <span data-ttu-id="f2e02-122">[逐步解說︰ 使用 BackgroundWorker 元件 (Visual Basic) 的多執行緒處理](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span><span class="sxs-lookup"><span data-stu-id="f2e02-122">[Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span></span>  
<span data-ttu-id="f2e02-123"> [執行緒集區 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md) </span><span class="sxs-lookup"><span data-stu-id="f2e02-123"> [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md) </span></span>  
<span data-ttu-id="f2e02-124"> [執行緒同步處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="f2e02-124"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
<span data-ttu-id="f2e02-125"> [事件](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="f2e02-125"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="f2e02-126"> [多執行緒應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="f2e02-126"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="f2e02-127"> [委派](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="f2e02-127"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="f2e02-128"> [多執行緒元件](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)</span><span class="sxs-lookup"><span data-stu-id="f2e02-128"> [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)</span></span>
