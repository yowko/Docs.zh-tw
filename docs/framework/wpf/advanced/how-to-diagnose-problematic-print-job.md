---
title: 如何：診斷問題列印工作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- troubleshooting print job problems [WPF]
- print jobs [WPF], troubleshooting
- print jobs [WPF], diagnosing problems
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
ms.openlocfilehash: 2010c911bd164570a82f23a939622f342810761f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546737"
---
# <a name="how-to-diagnose-problematic-print-job"></a>如何：診斷問題列印工作
網路系統管理經常處理使用者對於列印工作的相關抱怨 (不會列印或列印緩慢)。 一組豐富的列印工作中公開的屬性[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]Microsoft.NET framework 提供一種方法執行列印工作的快速遠端診斷。  
  
## <a name="example"></a>範例  
 建立這類公用程式的主要步驟如下所示。  
  
1.  找出使用者所抱怨的列印工作。 使用者通常無法準確地找出來。 他們可能不知道印表機的列印伺服器名稱。 它們可能會比用於設定說明在不同的術語印表機的位置及其<xref:System.Printing.PrintQueue.Location%2A>屬性。 因此，最好能產生使用者目前已提交的工作清單。 如果有多項工作，使用者與列印系統管理員之間的通訊則可用來指出有問題的工作。 子步驟如下所示。  
  
    1.  取得所有列印伺服器的清單。  
  
    2.  對伺服器執行迴圈，以查詢其列印佇列。  
  
    3.  在伺服器迴圈的每次操作中，對所有伺服器的佇列執行迴圈以查詢其工作。  
  
    4.  在佇列迴圈的每次操作中，對其工作執行迴圈並蒐集有關抱怨使用者所提出工作的識別資訊。  
  
2.  找出有問題的列印工作後，檢查相關屬性以了解問題所在。 例如，工作處於錯誤狀態，或者是為佇列提供服務的印表機在可列印工作之前離線？  
  
 下列程式碼是一系列的程式碼範例。 第一個程式碼範例包含列印佇列的迴圈執行。 (上面步驟 1c。)變數`myPrintQueues`是<xref:System.Printing.PrintQueueCollection>物件目前的列印伺服器。  
  
 程式碼範例會開始重新整理目前的列印佇列物件<xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>。 這可確保物件的屬性精確地呈現它所代表之實體印表機的狀態。 然後應用程式取得列印工作的集合目前列印佇列中使用<xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>。  
  
 應用程式中下一個循環<xref:System.Printing.PrintSystemJobInfo>集合並比較每個<xref:System.Printing.PrintSystemJobInfo.Submitter%2A>抱怨使用者別名的屬性。 如果兩者相符，應用程式會將有關工作的識別資訊新增至將要呈現的字串。 (`userName` 和 `jobList` 變數稍早已在應用程式中初始化。)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 下一個程式碼範例會在步驟 2 中挑選應用程式。 (請參閱上面的資訊。)已找出有問題的工作，而且應用程式提示輸入將用來識別該工作的資訊。 這項資訊建立<xref:System.Printing.PrintServer>， <xref:System.Printing.PrintQueue>，和<xref:System.Printing.PrintSystemJobInfo>物件。  
  
 此時應用程式包含一個分支結構，其對應於檢查列印工作狀態的兩種方法︰  
  
-   您可以閱讀的旗標<xref:System.Printing.PrintSystemJobInfo.JobStatus%2A>屬性的型別<xref:System.Printing.PrintJobStatus>。  
  
-   您可以閱讀每個相關的屬性，例如<xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A>和<xref:System.Printing.PrintSystemJobInfo.IsInError%2A>。  
  
 這個範例會示範這兩種方法，所以使用者先前已在提示確認要使用的方法，且回應為"Y"，如果他或她想要使用的旗標<xref:System.Printing.PrintSystemJobInfo.JobStatus%2A>屬性。 請參閱以下兩種方法的詳細資訊。 最後，應用程式會使用稱為 **ReportQueueAndJobAvailability** 的方法來報告是否可以在每天此時列印此工作。 [得知列印工作是否可在此時列印](../../../../docs/framework/wpf/advanced/how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md)會討論此方法。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 若要檢查使用的旗標的列印工作狀態<xref:System.Printing.PrintSystemJobInfo.JobStatus%2A>屬性，檢查是否設定每個相關旗標。 若要查看是否已在一組位元旗標中設定一個位元，標準方法就是以這組旗標做為一個運算元，而旗標本身做為另一個運算元來執行邏輯 AND 運算。 因為旗標本身只會設定一個位元，所以邏輯 AND 的結果是最多設定相同的位元。 若要查明是否如此，只要比較邏輯 AND 的結果與旗標本身。 如需詳細資訊，請參閱<xref:System.Printing.PrintJobStatus>、 [& 運算子 （C# 參考）](~/docs/csharp/language-reference/operators/and-operator.md)，和<xref:System.FlagsAttribute>。  
  
 對於已設定位元的每個屬性，程式碼會將此回報至主控台畫面，而且有時會建議回應方式。 (下面會討論工作或佇列暫停時所呼叫的 **HandlePausedJob** 方法。)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 若要使用不同的屬性來檢查列印工作狀態，您只要讀取每個屬性，如果屬性為 `true`，則會回報至主控台畫面並可能建議回應方式。 (下面會討論工作或佇列暫停時所呼叫的 **HandlePausedJob** 方法。)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** 方法可讓應用程式的使用者從遠端繼續進行已暫停的工作。 因為列印佇列暫停可能有充分的理由，所以此方法一開始會提示使用者決定是否要繼續進行。 如果回答都是"Y"，然後在<xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType>方法呼叫。  
  
 接著會提示使用者決定工作本身是否應該繼續進行，以防萬一其獨立暫停 (與列印佇列無關)。 (比較<xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType>和<xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>。)如果答案為"Y"，然後<xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType>呼叫; 否則為<xref:System.Printing.PrintSystemJobInfo.Cancel%2A>呼叫。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Printing.PrintJobStatus>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintQueue>  
 [& 運算子 （C# 參考）](~/docs/csharp/language-reference/operators/and-operator.md)  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)
