---
title: 如何：從遠端調查印表機的狀態
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: eca1720aea1620683ebc9ed08b47a0f5625da9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>如何：從遠端調查印表機的狀態
在任何時候，中型和大型公司都可能有多部印表機因為夾紙或紙張用完或一些其他問題狀況而無法運作。 一組豐富的印表機內容中公開[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]Microsoft.NET framework 提供一種方法執行快速問卷印表機的狀態。  
  
## <a name="example"></a>範例  
 建立這類公用程式的主要步驟如下所示。  
  
1.  取得所有列印伺服器的清單。  
  
2.  對伺服器執行迴圈，以查詢其列印佇列。  
  
3.  在伺服器迴圈的每次操作中，對所有伺服器的佇列執行迴圈，並讀取可能表示佇列目前不在運作中的每個屬性。  
  
 下列程式碼是一系列的程式碼片段。 為了簡單起見，本範例假設有列印伺服器的 CRLF 分隔清單。 變數`fileOfPrintServers`是<xref:System.IO.StreamReader>物件，這個檔案。 由於每個伺服器名稱的那一行，呼叫的<xref:System.IO.StreamReader.ReadLine%2A>取得下一部伺服器的名稱，並將移<xref:System.IO.StreamReader>的下一行的開頭的資料指標。  
  
 外部迴圈中，在程式碼會建立<xref:System.Printing.PrintServer>物件的最新的列印伺服器，並指定應用程式是以具有系統管理權限給伺服器。  
  
> [!NOTE]
>  如果有大量的伺服器，您可以使用來改善效能<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29>建構函式只會初始化您將需要的屬性。  
  
 然後此範例使用<xref:System.Printing.PrintServer.GetPrintQueues%2A>建立集合的所有伺服器的佇列，並開始其執行迴圈。 此內部迴圈包含一個分支結構，其對應於檢查印表機狀態的兩種方法︰  
  
-   您可以閱讀的旗標<xref:System.Printing.PrintQueue.QueueStatus%2A>屬性的型別<xref:System.Printing.PrintQueueStatus>。  
  
-   您可以閱讀每個相關的屬性，例如<xref:System.Printing.PrintQueue.IsOutOfPaper%2A>，和<xref:System.Printing.PrintQueue.IsPaperJammed%2A>。  
  
 這個範例會示範這兩種方法，所以使用者先前已在提示確認要使用的方法，且回應為"y"，如果他或她想要使用的旗標<xref:System.Printing.PrintQueue.QueueStatus%2A>屬性。 請參閱以下兩種方法的詳細資訊。  
  
 最後，結果會呈現給使用者。  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 若要檢查印表機狀態使用的旗標<xref:System.Printing.PrintQueue.QueueStatus%2A>屬性，檢查是否設定每個相關旗標。 若要查看是否已在一組位元旗標中設定一個位元，標準方法就是以這組旗標做為一個運算元，而旗標本身做為另一個運算元來執行邏輯 AND 運算。 因為旗標本身只會設定一個位元，所以邏輯 AND 的結果是最多設定相同的位元。 若要查明是否如此，只要比較邏輯 AND 的結果與旗標本身。 如需詳細資訊，請參閱<xref:System.Printing.PrintQueueStatus>、 [& 運算子 （C# 參考）](~/docs/csharp/language-reference/operators/and-operator.md)，和<xref:System.FlagsAttribute>。  
  
 對於已設定位元的每個屬性，程式碼會在將呈現給使用者的最終報告中加入注意事項。 (以下將討論在程式碼結尾呼叫的 **ReportAvailabilityAtThisTime** 方法。)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 若要使用每個屬性來檢查印表機狀態，您只要讀取每個屬性，而如果屬性為 `true`，則在將呈現給使用者的最終報告中加入注意事項。 (以下將討論在程式碼結尾呼叫的 **ReportAvailabilityAtThisTime** 方法。)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 已建立 **ReportAvailabilityAtThisTime** 方法，以防萬一您需要判斷目前是否可使用佇列。  
  
 方法會執行任何動作如果<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性相等，因為在此情況下印表機可用的所有權。 如果不相同，方法會取得目前的時間再轉換成午夜的總分鐘數，因為具有<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性<xref:System.Int32>不代表之後午夜分鐘<xref:System.DateTime>物件。 最後，此方法會檢查目前的時間是否介於開始與「直到」時間之間。  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintQueueStatus>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 [& 運算子 （C# 參考）](~/docs/csharp/language-reference/operators/and-operator.md)  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)
