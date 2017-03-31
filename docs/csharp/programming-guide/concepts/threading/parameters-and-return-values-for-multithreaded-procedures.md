---
title: "多執行緒程序的參數和傳回值 (C#) | Microsoft Docs"
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
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 95fdc0f74c1f2c35a4f3b5c0a8f40f5d4fe9457c
ms.lasthandoff: 03/13/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>多執行緒程序的參數和傳回值 (C#)
在多執行緒應用程式中提供和傳回值很複雜，因為執行緒類別的建構函式必須傳遞到不採用任何引數且不傳回任何值的程序參考。 下節會說明一些簡單的方法來提供參數，以及從不同執行緒的程序傳回值。  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>為多執行緒程序提供參數  
 為多執行緒方法呼叫提供參數的最佳方式，是將目標方法包裝在類別中，並為要用為新執行緒參數的類別定義欄位。 這種方法的優點是您可以建立類別的新執行個體，每次想要開始新執行緒都可以使用它自己的參數。 例如，假設您有計算三角形面積的函式，如下列程式碼所示︰  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 您可以撰寫類別，包裝 `CalcArea` 函式並建立儲存輸入參數的欄位，如下所示︰  
  
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
  
 若要使用 `AreaClass`，您可以建立 `AreaClass` 物件，然後設定 `Base` 和 `Height` 屬性，如下列程式碼所示︰  
  
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
  
 請注意，呼叫 `CalcArea` 方法之後，`TestArea` 程序不會檢查 `Area` 欄位的值。 如果您在呼叫 `Thread.Start` 之後立即檢查，因為 `CalcArea` 在另外的執行緒上執行，所以不保證會設定 `Area` 欄位。 下節會討論從多執行緒程序傳回值的更好方法。  
  
## <a name="returning-values-from-multithreaded-procedures"></a>從多執行緒程序傳回值  
 從在其他執行緒上執行的程序傳回值很複雜，因為這些程序不能是函式，也無法使用 `ByRef` 引數。 傳回值最簡單的方式是使用 <xref:System.ComponentModel.BackgroundWorker> 元件來管理您的執行緒，並在工作完成時引發事件，然後以事件處理常式來處理結果。  
  
 下例會透過從在另一個執行緒上執行的程序引發事件傳回值：  
  
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
  
 您可以使用 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> 方法的選擇性 `ByVal` 狀態物件變數，提供參數並將值傳回執行緒共用執行緒。 執行緒計時器執行緒也支援針對此目的狀態物件。 如需執行緒共用和執行緒計時器的資訊，請參閱[執行緒共用 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)和[執行緒計時器 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：使用 BackgroundWorker 元件進行多執行緒處理 (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)   
 [執行緒共用 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)   
 [執行緒同步處理 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)   
 [事件](../../../../csharp/programming-guide/events/index.md)   
 [多執行緒應用程式 (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)   
 [委派](../../../../csharp/programming-guide/delegates/index.md)   
 [元件中的多執行緒](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
