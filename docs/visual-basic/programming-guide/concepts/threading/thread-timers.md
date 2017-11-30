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
# <a name="thread-timers-visual-basic"></a>執行緒計時器 (Visual Basic)
<xref:System.Threading.Timer?displayProperty=nameWithType> 類別適用於定期對不同的執行緒執行工作。 例如，您可以使用執行緒計時器來檢查資料庫的狀態和完整性，或備份重要檔案。  
  
## <a name="thread-timer-example"></a>執行緒計時器範例  
 下列範例會每隔兩秒鐘啟動一次工作，並使用旗標來起始會停止計時器的 <xref:System.IDisposable.Dispose%2A> 方法。 這個範例會將狀態公佈至輸出視窗。  
  
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
  
 <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> 物件無法使用時，執行緒計時器特別有用，例如開發主控台應用程式時。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading>  
 [多執行緒應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)
