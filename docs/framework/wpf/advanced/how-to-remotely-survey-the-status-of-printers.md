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
ms.openlocfilehash: 859ccb703c6c54c66d6ea7b433c67d156627e25b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187030"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>如何：從遠端調查印表機的狀態
在任何時候，中型和大型公司都可能有多部印表機因為夾紙或紙張用完或一些其他問題狀況而無法運作。 Microsoft .NET Framework API 中公開的豐富的印表機屬性集提供了一種快速調查印表機狀態的方法。  
  
## <a name="example"></a>範例  
 建立這類公用程式的主要步驟如下所示。  
  
1. 取得所有列印伺服器的清單。  
  
2. 對伺服器執行迴圈，以查詢其列印佇列。  
  
3. 在伺服器迴圈的每次操作中，對所有伺服器的佇列執行迴圈，並讀取可能表示佇列目前不在運作中的每個屬性。  
  
 下列程式碼是一系列的程式碼片段。 為了簡單起見，本範例假設有列印伺服器的 CRLF 分隔清單。 變數`fileOfPrintServers`是<xref:System.IO.StreamReader>此檔的物件。 由於每個伺服器名稱都位於其自己的行上，因此<xref:System.IO.StreamReader.ReadLine%2A>，任何調用 都會獲取下一個伺服器<xref:System.IO.StreamReader>的名稱，並將 游標移動到下一行的開頭。  
  
 在外部迴圈中，代碼為最新的列印<xref:System.Printing.PrintServer>伺服器創建一個物件，並指定應用程式對伺服器具有管理許可權。  
  
> [!NOTE]
> 如果伺服器很多，則可以使用僅初始化所需屬性的<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29>建構函式來提高性能。  
  
 然後，該示例<xref:System.Printing.PrintServer.GetPrintQueues%2A>用於創建伺服器的所有佇列的集合，並開始逐一查看這些佇列。 此內部迴圈包含一個分支結構，其對應於檢查印表機狀態的兩種方法︰  
  
- 可以讀取 類型<xref:System.Printing.PrintQueue.QueueStatus%2A><xref:System.Printing.PrintQueueStatus>的屬性的標誌。  
  
- 可以讀取每個相關屬性，如<xref:System.Printing.PrintQueue.IsOutOfPaper%2A>和<xref:System.Printing.PrintQueue.IsPaperJammed%2A>。  
  
 此示例演示了這兩種方法，因此之前系統會提示使用者使用哪種方法，如果使用者想要使用<xref:System.Printing.PrintQueue.QueueStatus%2A>屬性的標誌，則使用"y"回應。 請參閱以下兩種方法的詳細資訊。  
  
 最後，結果會呈現給使用者。  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 要使用<xref:System.Printing.PrintQueue.QueueStatus%2A>屬性的標誌檢查印表機狀態，請檢查每個相關標誌以查看是否已設置。 若要查看是否已在一組位元旗標中設定一個位元，標準方法就是以這組旗標做為一個運算元，而旗標本身做為另一個運算元來執行邏輯 AND 運算。 因為旗標本身只會設定一個位元，所以邏輯 AND 的結果是最多設定相同的位元。 若要查明是否如此，只要比較邏輯 AND 的結果與旗標本身。 有關詳細資訊，請參閱<xref:System.Printing.PrintQueueStatus> [& 運算子 （C# 參考）](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)和<xref:System.FlagsAttribute>。  
  
 對於已設定位元的每個屬性，程式碼會在將呈現給使用者的最終報告中加入注意事項。 (以下將討論在程式碼結尾呼叫的 **ReportAvailabilityAtThisTime** 方法。)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 若要使用每個屬性來檢查印表機狀態，您只要讀取每個屬性，而如果屬性為 `true`，則在將呈現給使用者的最終報告中加入注意事項。 (以下將討論在程式碼結尾呼叫的 **ReportAvailabilityAtThisTime** 方法。)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 已建立 **ReportAvailabilityAtThisTime** 方法，以防萬一您需要判斷目前是否可使用佇列。  
  
 如果 和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性相等，<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>則 該方法將不執行任何操作;因為在這種情況下，印表機隨時可用。 如果它們不同，該方法獲取目前時間，然後必須轉換成午夜後的總<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>分鐘數，因為 和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性工作表示<xref:System.Int32>午夜後幾分鐘，而不是<xref:System.DateTime>物件。 最後，此方法會檢查目前的時間是否介於開始與「直到」時間之間。  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>
- <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>
- <xref:System.DateTime>
- <xref:System.Printing.PrintQueueStatus>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- [&運算子（C# 參考）](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
