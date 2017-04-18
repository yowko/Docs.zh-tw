---
title: "如何：診斷問題列印工作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "列印工作, 診斷問題"
  - "列印工作, 疑難排解"
  - "列印工作問題疑難排解"
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：診斷問題列印工作
網路系統管理員經常要處理使用者對列印工作的抱怨，如無法列印或列印得很慢。  [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 的 [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] 中公開一組豐富的列印工作屬性 \(Property\)，可用以執行列印工作的快速遠端診斷。  
  
## 範例  
 建立這類公用程式的主要步驟如下。  
  
1.  識別使用者抱怨的列印工作。  使用者通常無法精確地做到這一點。  他們可能不知道列印伺服器或印表機的名稱。  他們會用不同的說法來描述印表機的位置，但不會說出印表機 <xref:System.Printing.PrintQueue.Location%2A> 屬性 \(Property\) 的設定值。  因此，最好是產生一張使用者目前已送出工作的清單。  如果已送出的工作不止一個，使用者和列印系統管理員可以互相連絡以找出有問題的工作。  詳細步驟如下：  
  
    1.  取得所有列印伺服器的清單。  
  
    2.  在各伺服器之間執行迴圈 \(Loop\)，查詢其列印佇列。  
  
    3.  在伺服器迴圈的每一次傳遞中，在伺服器的所有佇列之間執行迴圈，查詢它們的工作。  
  
    4.  在佇列迴圈的每一次傳遞中，在其工作之間執行迴圈，並收集抱怨的使用者送出的工作的識別資訊。  
  
2.  找出有問題的列印工作後，檢查相關的屬性 \(Property\)，看看可能是什麼問題。  例如，工作是否在錯誤狀態之下？或處理這個佇列的印表機在列印工作開始前就離線了？  
  
 下列程式碼是一系列程式碼範例。  第一個程式碼範例是在列印佇列之間執行的迴圈   \(上述的步驟 1c\)。 變數 `myPrintQueues` 是目前列印伺服器的 <xref:System.Printing.PrintQueueCollection> 物件。  
  
 程式碼範例一開始先用 <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=fullName> 重新整理目前的列印佇列物件。  這可確保物件的屬性 \(Property\) 正確地表示它所代表的實體印表機的狀態。  然後應用程式使用 <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A> 取得目前在列印佇列中的列印工作的集合。  
  
 接著應用程式在整個 <xref:System.Printing.PrintSystemJobInfo> 集合中執行迴圈，比較每個 <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> 屬性 \(Property\) 與抱怨使用者的別名。  如果相符，應用程式就會將這個工作的識別資訊加入即將顯示的字串中   \(`userName` 和 `jobList` 變數稍早已在應用程式中初始化\)。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 下一個程式碼範例會在步驟 2 挑選應用程式  \(如上所述\)。 找出有問題的工作後，應用程式會提示您輸入可識別該工作的資訊。  它會從這些資訊建立 <xref:System.Printing.PrintServer>、<xref:System.Printing.PrintQueue> 和 <xref:System.Printing.PrintSystemJobInfo> 物件。  
  
 此時的應用程式包含分支結構，與檢查列印工作狀態的兩種方式相對應：  
  
-   您可以查看 <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> 屬性 \(Property\) 的旗標，這個屬性是 <xref:System.Printing.PrintJobStatus> 型別。  
  
-   您可以查看每個相關的屬性 \(Property\)，如 <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> 和 <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>。  
  
 這個範例示範了這兩種方法，因此使用者會在稍早收到要選擇哪個方法來使用的提示，並在要用 <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> 屬性 \(Property\) 的旗標時回應 "Y"。  請看以下對兩種方法的詳細說明。  最後，應用程式使用 **ReportQueueAndJobAvailability** 方法報告這個工作是否可以在今天這個時刻進行列印。  這個方法在 [得知列印工作是否可在此時列印](../../../../docs/framework/wpf/advanced/how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md)中討論。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 若要用 <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> 屬性 \(Property\) 的旗標檢查列印工作狀態，請檢查每一個相關旗標，看它是否有設定。  若要查看一組位元旗標中是否設定位元，標準的做法是執行邏輯 AND 運算，以這組旗標做為一個運算元，旗標本身則做為另一個運算元。  因為旗標本身只設定一個位元，所以邏輯 AND 運算的結果最多會設定相同的位元。  若要找出是否已設定該位元，則只要比較邏輯 AND 的結果和旗標本身即可。  如需詳細資訊，請參閱 <xref:System.Printing.PrintJobStatus>、[& 運算子 \(C\# 參考\)](../Topic/&%20Operator%20\(C%23%20Reference\).md) 和 <xref:System.FlagsAttribute>。  
  
 程式碼會將每一個有設定位元的屬性 \(Attribute\) 報告至主控台螢幕中，而且有時候會建議回應的方式   \(如果工作或佇列已暫停，就是 **HandlePausedJob** 方法，稍後討論此方法\)。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 若要用個別的屬性 \(Property\) 檢查列印工作狀態，您只需要看每一個屬性，如果屬性為 `true`，就會報告至主控台螢幕中，而且可能會建議回應方式   \(如果工作或佇列已暫停，就是 **HandlePausedJob** 方法，稍後討論此方法\)。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** 方法讓應用程式的使用者可以從遠端恢復暫停的工作。  因為列印佇列暫停可能有個好理由，這個方法一開始會提示使用者決定是否要繼續工作。  如果答案是 "Y"，就會呼叫 <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=fullName> 方法。  
  
 接著會提示使用者決定工作本身是否應當繼續，以防萬一工作的暫停和列印佇列無關   \(比較 <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=fullName> 和 <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=fullName>\)。 如果答案是 "Y"，就會呼叫 <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=fullName>，若不是則呼叫 <xref:System.Printing.PrintSystemJobInfo.Cancel%2A>。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## 請參閱  
 <xref:System.Printing.PrintJobStatus>   
 <xref:System.Printing.PrintSystemJobInfo>   
 <xref:System.FlagsAttribute>   
 <xref:System.Printing.PrintQueue>   
 [& 運算子 \(C\# 參考\)](../Topic/&%20Operator%20\(C%23%20Reference\).md)   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)