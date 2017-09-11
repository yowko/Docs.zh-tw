---
title: "執行緒計時器 (C#) | Microsoft Docs"
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
ms.assetid: 52ed71e8-4fd9-43a4-ae40-04cce7cff23f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 2f81e7f8b87db58958faf29f34598d44c3f671c6
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="thread-timers-c"></a><span data-ttu-id="699e6-102">執行緒計時器 (C#)</span><span class="sxs-lookup"><span data-stu-id="699e6-102">Thread Timers (C#)</span></span>
<span data-ttu-id="699e6-103"><xref:System.Threading.Timer?displayProperty=fullName> 類別適用於在個別執行緒上定期執行工作。</span><span class="sxs-lookup"><span data-stu-id="699e6-103">The <xref:System.Threading.Timer?displayProperty=fullName> class is useful for periodically running a task on a separate thread.</span></span> <span data-ttu-id="699e6-104">例如，您可以使用執行緒計時器來檢查資料庫的狀態和完整性，或備份重要檔案。</span><span class="sxs-lookup"><span data-stu-id="699e6-104">For example, you could use a thread timer to check the status and integrity of a database or to back up critical files.</span></span>  
  
## <a name="thread-timer-example"></a><span data-ttu-id="699e6-105">執行緒計時器範例</span><span class="sxs-lookup"><span data-stu-id="699e6-105">Thread Timer Example</span></span>  
 <span data-ttu-id="699e6-106">下列範例會每隔兩秒鐘啟動一次工作，並使用旗標來起始會停止計時器的 <xref:System.IDisposable.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="699e6-106">The following example starts a task every two seconds and uses a flag to initiate the <xref:System.IDisposable.Dispose%2A> method that stops the timer.</span></span> <span data-ttu-id="699e6-107">這個範例會將狀態公佈至輸出視窗。</span><span class="sxs-lookup"><span data-stu-id="699e6-107">This example posts status to the output window.</span></span>  
  
```csharp  
private class StateObjClass  
{  
    // Used to hold parameters for calls to TimerTask.  
    public int SomeValue;  
    public System.Threading.Timer TimerReference;  
    public bool TimerCanceled;  
}  
  
public void RunTimer()  
{  
    StateObjClass StateObj = new StateObjClass();  
    StateObj.TimerCanceled = false;  
    StateObj.SomeValue = 1;  
    System.Threading.TimerCallback TimerDelegate =  
        new System.Threading.TimerCallback(TimerTask);  
  
    // Create a timer that calls a procedure every 2 seconds.  
    // Note: There is no Start method; the timer starts running as soon as   
    // the instance is created.  
    System.Threading.Timer TimerItem =  
        new System.Threading.Timer(TimerDelegate, StateObj, 2000, 2000);  
  
    // Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem;    
  
    // Run for ten loops.  
    while (StateObj.SomeValue < 10)   
    {  
        // Wait one second.  
        System.Threading.Thread.Sleep(1000);    
    }  
  
    // Request Dispose of the timer object.  
    StateObj.TimerCanceled = true;    
}  
  
private void TimerTask(object StateObj)  
{  
    StateObjClass State = (StateObjClass)StateObj;  
    // Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(ref State.SomeValue);  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " + DateTime.Now.ToString());  
    if (State.TimerCanceled)      
    // Dispose Requested.  
    {  
        State.TimerReference.Dispose();  
        System.Diagnostics.Debug.WriteLine("Done  " + DateTime.Now.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="699e6-108"><xref:System.Windows.Forms.Timer?displayProperty=fullName> 物件無法使用時，執行緒計時器特別有用，例如開發主控台應用程式時。</span><span class="sxs-lookup"><span data-stu-id="699e6-108">Thread timers are particularly useful when the <xref:System.Windows.Forms.Timer?displayProperty=fullName> object is unavailable, such as when you are developing console applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699e6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="699e6-109">See Also</span></span>  
 <span data-ttu-id="699e6-110"><xref:System.Threading></span><span class="sxs-lookup"><span data-stu-id="699e6-110"><xref:System.Threading></span></span>   
<span data-ttu-id="699e6-111"> [多執行緒應用程式 (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)</span><span class="sxs-lookup"><span data-stu-id="699e6-111"> [Multithreaded Applications (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)</span></span>
