---
title: "執行緒計時器 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 809cba93-cc93-4e21-afda-f299f9a39818
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b828476301424ca767e2b581c173d6a2dcd184ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="thread-timers-visual-basic"></a><span data-ttu-id="a37d7-102">執行緒計時器 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a37d7-102">Thread Timers (Visual Basic)</span></span>
<span data-ttu-id="a37d7-103"><xref:System.Threading.Timer?displayProperty=nameWithType> 類別適用於定期對不同的執行緒執行工作。</span><span class="sxs-lookup"><span data-stu-id="a37d7-103">The <xref:System.Threading.Timer?displayProperty=nameWithType> class is useful for periodically running a task on a separate thread.</span></span> <span data-ttu-id="a37d7-104">例如，您可以使用執行緒計時器來檢查資料庫的狀態和完整性，或備份重要檔案。</span><span class="sxs-lookup"><span data-stu-id="a37d7-104">For example, you could use a thread timer to check the status and integrity of a database or to back up critical files.</span></span>  
  
## <a name="thread-timer-example"></a><span data-ttu-id="a37d7-105">執行緒計時器範例</span><span class="sxs-lookup"><span data-stu-id="a37d7-105">Thread Timer Example</span></span>  
 <span data-ttu-id="a37d7-106">下列範例會每隔兩秒鐘啟動一次工作，並使用旗標來起始會停止計時器的 <xref:System.IDisposable.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a37d7-106">The following example starts a task every two seconds and uses a flag to initiate the <xref:System.IDisposable.Dispose%2A> method that stops the timer.</span></span> <span data-ttu-id="a37d7-107">這個範例會將狀態公佈至輸出視窗。</span><span class="sxs-lookup"><span data-stu-id="a37d7-107">This example posts status to the output window.</span></span>  
  
```vb  
Private Class StateObjClass  
    ' Used to hold parameters for calls to TimerTask.  
    Public SomeValue As Integer  
    Public TimerReference As System.Threading.Timer  
    Public TimerCanceled As Boolean  
End Class  
  
Public Sub RunTimer()  
    Dim StateObj As New StateObjClass  
    StateObj.TimerCanceled = False  
    StateObj.SomeValue = 1  
    Dim TimerDelegate As New System.Threading.TimerCallback(AddressOf TimerTask)  
    ' Create a timer that calls a procedure every 2 seconds.  
    ' Note: There is no Start method; the timer starts running as soon as   
    ' the instance is created.  
    Dim TimerItem As New System.Threading.Timer(TimerDelegate, StateObj,  
                                                2000, 2000)  
    ' Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem  
  
    ' Run for ten loops.  
    While StateObj.SomeValue < 10  
        ' Wait one second.  
        System.Threading.Thread.Sleep(1000)  
    End While  
  
    ' Request Dispose of the timer object.  
    StateObj.TimerCanceled = True  
End Sub  
  
Private Sub TimerTask(ByVal StateObj As Object)  
    Dim State As StateObjClass = CType(StateObj, StateObjClass)  
    ' Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(State.SomeValue)  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " & Now.ToString)  
    If State.TimerCanceled Then  
        ' Dispose Requested.  
        State.TimerReference.Dispose()  
        System.Diagnostics.Debug.WriteLine("Done  " & Now)  
    End If  
End Sub  
```  
  
 <span data-ttu-id="a37d7-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType> 物件無法使用時，執行緒計時器特別有用，例如開發主控台應用程式時。</span><span class="sxs-lookup"><span data-stu-id="a37d7-108">Thread timers are particularly useful when the <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> object is unavailable, such as when you are developing console applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a37d7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a37d7-109">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="a37d7-110">多執行緒應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a37d7-110">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)
