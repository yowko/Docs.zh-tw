---
title: "多執行緒應用程式 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5bde7f49a2f2bc8a2e6c1eeab3722428b8a37a95
ms.lasthandoff: 03/13/2017

---
# <a name="multithreaded-applications-visual-basic"></a>多執行緒應用程式 (Visual Basic)
使用 Visual Basic 中，您可以撰寫同時執行多個工作的應用程式。 可能會妨礙其他工作的工作可以執行個別的執行緒上這道程序*多執行緒*或*釋放執行緒*。  
  
 使用多執行緒會更快速地回應使用者輸入，因為使用者介面保持使用中，因為處理器密集工作在個別執行緒上執行的應用程式。 多執行緒處理時，也建立可擴充的應用程式，因為您可以在工作負載增加時加入執行緒。  
  
## <a name="creating-and-using-threads"></a>建立和使用執行緒  
 如果您需要更充分掌控您的應用程式執行緒的行為，您可以自行管理執行緒。 然而，了解撰寫正確的多執行緒應用程式十分困難︰ 您的應用程式可能會停止回應或發生競爭情形所造成的暫時性錯誤。 如需詳細資訊，請參閱[安全執行緒的元件](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)。  
  
 宣告型別的變數建立新的執行緒<xref:System.Threading.Thread>和提供的程序或您想要在新的執行緒上執行的方法名稱的建構函式。</xref:System.Threading.Thread> 下列程式碼提供一個範例。  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### <a name="starting-and-stopping-threads"></a>啟動和停止執行緒  
 若要啟動新執行緒的執行，請使用<xref:System.Threading.Thread.Start%2A>方法，如下列程式碼所示。</xref:System.Threading.Thread.Start%2A>  
  
```vb  
newThread.Start()  
```  
  
 若要停止的執行緒執行，請使用<xref:System.Threading.Thread.Abort%2A>方法，如下列程式碼所示。</xref:System.Threading.Thread.Abort%2A>  
  
```vb  
newThread.Abort()  
```  
  
 除了啟動和停止執行緒，您也可以暫停執行緒藉由呼叫<xref:System.Threading.Thread.Sleep%2A>或<xref:System.Threading.Thread.Suspend%2A>方法中，使用恢復暫停的執行緒<xref:System.Threading.Thread.Resume%2A>方法，和使用的<xref:System.Threading.Thread.Abort%2A>方法</xref:System.Threading.Thread.Abort%2A>終結執行緒</xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Sleep%2A>  
  
### <a name="thread-methods"></a>執行緒方法  
 下表顯示一些可用來控制的個別執行緒的方法。  
  
|方法|動作|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A>|使執行緒開始執行。|  
|<xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A>|暫停執行緒，在指定的時間。|  
|<xref:System.Threading.Thread.Suspend%2A></xref:System.Threading.Thread.Suspend%2A>|當它到達安全點暫停執行緒。|  
|<xref:System.Threading.Thread.Abort%2A></xref:System.Threading.Thread.Abort%2A>|當它到達安全點停止執行緒。|  
|<xref:System.Threading.Thread.Resume%2A></xref:System.Threading.Thread.Resume%2A>|重新啟動暫止的執行緒|  
|<xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A>|造成等候另一個執行緒完成目前的執行緒。 如果搭配使用的逾時值，此方法會傳回`True`如果執行緒配置的時間內完成。|  
  
### <a name="safe-points"></a>安全點  
 這些方法大多都一目了然，但概念的*安全點*可能不熟悉。 安全點是很安全的 common language runtime 來執行自動程式碼中位置*回收*，釋放未使用的變數，並回收記憶體的程序。 當您呼叫<xref:System.Threading.Thread.Abort%2A>或<xref:System.Threading.Thread.Suspend%2A>方法的執行緒，common language runtime 會分析程式碼，並決定適當的位置停止執行的執行緒的位置。</xref:System.Threading.Thread.Suspend%2A> </xref:System.Threading.Thread.Abort%2A>  
  
### <a name="thread-properties"></a>執行緒屬性  
 執行緒也包含許多有用的內容下, 表所示︰  
  
|屬性|值|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A></xref:System.Threading.Thread.IsAlive%2A>|包含值`True`如果執行緒在作用中。|  
|<xref:System.Threading.Thread.IsBackground%2A></xref:System.Threading.Thread.IsBackground%2A>|取得或設定布林值，表示是否執行緒或應該是背景執行緒。 背景執行緒就像前景執行緒一樣，但是背景執行緒無法停止防止處理程序。 停止所有處理程序所屬的前景執行緒之後，common language runtime 會藉由呼叫結束處理序<xref:System.Threading.Thread.Abort%2A>仍在執行的背景執行緒上的方法。</xref:System.Threading.Thread.Abort%2A>|  
|<xref:System.Threading.Thread.Name%2A></xref:System.Threading.Thread.Name%2A>|取得或設定執行緒的名稱。 最常用於探索的個別執行緒，當您偵錯。|  
|<xref:System.Threading.Thread.Priority%2A></xref:System.Threading.Thread.Priority%2A>|取得或設定值，這個值，可由作業系統執行緒排程的優先順序。|  
|<xref:System.Threading.Thread.ThreadState%2A></xref:System.Threading.Thread.ThreadState%2A>|包含說明執行緒的狀態的值。|  
  
## <a name="thread-priorities"></a>執行緒優先順序  
 每個執行緒都有 priority 屬性，用於判斷多少處理器時間後執行。 作業系統會配置較長的時間配量，以高優先順序的執行緒和較短的時間配量，以低優先順序的執行緒。 建立新的執行緒，其值為`Normal`，但是您可以變更<xref:System.Threading.Thread.Priority%2A>屬性中的任何值<xref:System.Threading.ThreadPriority>列舉型別。</xref:System.Threading.ThreadPriority> </xref:System.Threading.Thread.Priority%2A>  
  
 請參閱<xref:System.Threading.ThreadPriority>的各種不同的執行緒優先順序的詳細說明。</xref:System.Threading.ThreadPriority>  
  
## <a name="foreground-and-background-threads"></a>前景和背景執行緒  
 A*幕前執行緒*無限期地執行，而*背景執行緒*會停止，因為最後一個幕前執行緒已停止。 您可以使用<xref:System.Threading.Thread.IsBackground%2A>屬性來判斷或變更背景執行緒的狀態。</xref:System.Threading.Thread.IsBackground%2A>  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread></xref:System.Threading.Thread>   
 [執行緒同步處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)   
 [參數和傳回值的多執行緒程序 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)   
 [執行緒處理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)
