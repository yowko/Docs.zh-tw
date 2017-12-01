---
title: "終結執行緒"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a41dce5db707d0be49c283256de665d316e1a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="destroying-threads"></a>終結執行緒
<xref:System.Threading.Thread.Abort%2A>方法用來永久停止 managed 的執行緒。 當您呼叫<xref:System.Threading.Thread.Abort%2A>，common language runtime 會擲回<xref:System.Threading.ThreadAbortException>中，在此目標執行緒可能會攔截目標執行緒。 如需詳細資訊，請參閱<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>。  
  
> [!NOTE]
>  如果執行緒正在執行 unmanaged 程式碼時其<xref:System.Threading.Thread.Abort%2A>呼叫方法時，執行階段會將其標示<xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>。 執行緒傳回給 managed 程式碼時，會擲回例外狀況。  
  
 一旦執行緒已中止時，它在重新啟動電腦。  
  
 <xref:System.Threading.Thread.Abort%2A>方法不會造成執行緒中止，因為目標執行緒可能會攔截<xref:System.Threading.ThreadAbortException>並執行程式碼中的任意數量`finally`區塊。 您可以呼叫<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>如果您需要等候，直到執行緒已結束。 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>封鎖呼叫執行緒已實際停止執行之前不會傳回或選用的逾時間隔已經耗盡。 已中止的執行緒可以呼叫<xref:System.Threading.Thread.ResetAbort%2A>方法或執行中的未繫結的處理`finally`區塊中，因此如果您未指定逾時，不保證結束等候。  
  
 等待在呼叫的執行緒<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>方法可以中斷由其他執行緒呼叫<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>。  
  
## <a name="handling-threadabortexception"></a>處理 ThreadAbortException  
 如果您預期您的執行緒會中止，呼叫的結果為<xref:System.Threading.Thread.Abort%2A>從自己的程式碼或執行後卸載應用程式定義域的執行緒已執行 (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>使用<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>終止執行緒)，您的執行緒必須處理<xref:System.Threading.ThreadAbortException>並執行中的任何最終處理`finally`子句，如下列程式碼所示。  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 清除程式碼必須在`catch`子句或`finally`子句，因為<xref:System.Threading.ThreadAbortException>重新擲回由系統在結尾`finally`子句，或結尾處`catch`子句如果沒有任何`finally`子句。  
  
 您可以防止重新例外狀況擲回藉由呼叫系統<xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>方法。 但是，您應該採取此只有當您自己的程式碼造成<xref:System.Threading.ThreadAbortException>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [使用執行緒和執行緒處理](../../../docs/standard/threading/using-threads-and-threading.md)
