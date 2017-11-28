---
title: "多執行緒程序的參數和傳回值 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fec0ad955439f0cd683ad56c8d6433eed2417304
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a><span data-ttu-id="4b782-102">多執行緒程序的參數和傳回值 (C#)</span><span class="sxs-lookup"><span data-stu-id="4b782-102">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>
<span data-ttu-id="4b782-103">在多執行緒應用程式中提供和傳回值很複雜，因為執行緒類別的建構函式必須傳遞到不採用任何引數且不傳回任何值的程序參考。</span><span class="sxs-lookup"><span data-stu-id="4b782-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="4b782-104">下節會說明一些簡單的方法來提供參數，以及從不同執行緒的程序傳回值。</span><span class="sxs-lookup"><span data-stu-id="4b782-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="4b782-105">為多執行緒程序提供參數</span><span class="sxs-lookup"><span data-stu-id="4b782-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="4b782-106">為多執行緒方法呼叫提供參數的最佳方式，是將目標方法包裝在類別中，並為要用為新執行緒參數的類別定義欄位。</span><span class="sxs-lookup"><span data-stu-id="4b782-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="4b782-107">這種方法的優點是您可以建立類別的新執行個體，每次想要開始新執行緒都可以使用它自己的參數。</span><span class="sxs-lookup"><span data-stu-id="4b782-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="4b782-108">例如，假設您有計算三角形面積的函式，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="4b782-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 <span data-ttu-id="4b782-109">您可以撰寫類別，包裝 `CalcArea` 函式並建立儲存輸入參數的欄位，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="4b782-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```csharp  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="4b782-110">若要使用 `AreaClass`，您可以建立 `AreaClass` 物件，然後設定 `Base` 和 `Height` 屬性，如下列程式碼所示︰</span><span class="sxs-lookup"><span data-stu-id="4b782-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```csharp  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 <span data-ttu-id="4b782-111">請注意，呼叫 `CalcArea` 方法之後，`TestArea` 程序不會檢查 `Area` 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="4b782-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="4b782-112">如果您在呼叫 `Thread.Start` 之後立即檢查，因為 `CalcArea` 在另外的執行緒上執行，所以不保證會設定 `Area` 欄位。</span><span class="sxs-lookup"><span data-stu-id="4b782-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="4b782-113">下節會討論從多執行緒程序傳回值的更好方法。</span><span class="sxs-lookup"><span data-stu-id="4b782-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="4b782-114">從多執行緒程序傳回值</span><span class="sxs-lookup"><span data-stu-id="4b782-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="4b782-115">從在其他執行緒上執行的程序傳回值很複雜，因為這些程序不能是函式，也無法使用 `ByRef` 引數。</span><span class="sxs-lookup"><span data-stu-id="4b782-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="4b782-116">傳回值最簡單的方式是使用 <xref:System.ComponentModel.BackgroundWorker> 元件來管理您的執行緒，並在工作完成時引發事件，然後以事件處理常式來處理結果。</span><span class="sxs-lookup"><span data-stu-id="4b782-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="4b782-117">下例會透過從在另一個執行緒上執行的程序引發事件傳回值：</span><span class="sxs-lookup"><span data-stu-id="4b782-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```csharp  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 <span data-ttu-id="4b782-118">您可以使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法的選擇性 `ByVal` 狀態物件變數，提供參數並將值傳回給執行緒集區執行緒。</span><span class="sxs-lookup"><span data-stu-id="4b782-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="4b782-119">執行緒計時器執行緒也支援針對此目的狀態物件。</span><span class="sxs-lookup"><span data-stu-id="4b782-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="4b782-120">如需執行緒共用和執行緒計時器的資訊，請參閱[執行緒共用 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)和[執行緒計時器 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)。</span><span class="sxs-lookup"><span data-stu-id="4b782-120">For information on thread pooling and thread timers, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) and [Thread Timers (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b782-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b782-121">See Also</span></span>  
 [<span data-ttu-id="4b782-122">逐步解說：BackgroundWorker 元件的多執行緒 (C#)</span><span class="sxs-lookup"><span data-stu-id="4b782-122">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="4b782-123">執行緒集區 (C#)</span><span class="sxs-lookup"><span data-stu-id="4b782-123">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="4b782-124">執行緒同步處理 (C#)</span><span class="sxs-lookup"><span data-stu-id="4b782-124">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="4b782-125">事件</span><span class="sxs-lookup"><span data-stu-id="4b782-125">Events</span></span>](../../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="4b782-126">多執行緒應用程式 (C#)</span><span class="sxs-lookup"><span data-stu-id="4b782-126">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="4b782-127">委派</span><span class="sxs-lookup"><span data-stu-id="4b782-127">Delegates</span></span>](../../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="4b782-128">元件中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="4b782-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
