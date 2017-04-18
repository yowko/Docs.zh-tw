---
title: "如何：從遠端調查印表機的狀態 | Microsoft Docs"
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
  - "印表機狀態, 遠端調查"
  - "從遠端調查印表機的狀態"
  - "狀態, 印表機, 遠端調查"
  - "從遠端調查印表機的狀態"
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：從遠端調查印表機的狀態
在中型和大型公司中，任何指定的時間內可能都會有多部印表機因卡紙、缺紙或其他某個問題狀況而未作用。  [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 的 [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] 中公開一組豐富的印表機屬性，提供方法來執行印表機狀態的快速調查。  
  
## 範例  
 建立這類公用程式的主要步驟如下。  
  
1.  取得所有列印伺服器的清單。  
  
2.  在各伺服器之間執行迴圈 \(Loop\)，查詢其列印佇列。  
  
3.  在伺服器迴圈的每次傳遞中，會在所有伺服器佇列之間執行迴圈，以及讀取可能表示佇列目前未作用的每個屬性。  
  
 下列程式碼是程式碼片段的一部分。  為了簡化，這個範例假設具有以 CRLF 分隔的列印伺服器清單。  變數 `fileOfPrintServers` 是這個檔案的 <xref:System.IO.StreamReader> 物件。  因為每個伺服器名稱都有它自己的一行，所以任何 <xref:System.IO.StreamReader.ReadLine%2A> 呼叫都會取得下一部伺服器的名稱，並將 <xref:System.IO.StreamReader> 的游標移至下一行的開頭。  
  
 在外部迴圈中，程式碼會針對最後一部列印伺服器建立 <xref:System.Printing.PrintServer> 物件，並指定應用程式需要具有伺服器的管理權限。  
  
> [!NOTE]
>  如果有多部伺服器，則可以使用只會初始化所需要屬性的 [PrintServer\(String, String\<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> 建構函式，以改善效能。  
  
 這個範例接著會使用 <xref:System.Printing.PrintServer.GetPrintQueues%2A> 來建立所有伺服器佇列的集合，並開始對它們執行迴圈。  這個內部迴圈包含分支結構，而這個分支結構與檢查印表機狀態的兩種方式相對應：  
  
-   您可以讀取型別為 <xref:System.Printing.PrintQueueStatus> 之 <xref:System.Printing.PrintQueue.QueueStatus%2A> 屬性的旗標。  
  
-   您可以讀取每個相關的屬性 \(如 <xref:System.Printing.PrintQueue.IsOutOfPaper%2A> 和 <xref:System.Printing.PrintQueue.IsPaperJammed%2A>\)。  
  
 這個範例示範這兩種方法，因此應用程式會先提示使用者選擇使用其中一種方法，並會在使用者想要使用 <xref:System.Printing.PrintQueue.QueueStatus%2A> 屬性的旗標時，回應 "y"。  請看以下對兩種方法的詳細說明。  
  
 最後，結果會呈現給使用者。  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 若要使用 <xref:System.Printing.PrintQueue.QueueStatus%2A> 屬性的旗標檢查印表機狀態，則請檢查每個相關旗標，查看是否已設定。  若要查看一組位元旗標中是否設定位元，標準的做法是執行邏輯 AND 運算，以這組旗標做為一個運算元，旗標本身則做為另一個運算元。  因為旗標本身只設定一個位元，所以邏輯 AND 運算的結果最多會設定相同的位元。  若要找出是否已設定該位元，則只要比較邏輯 AND 的結果和旗標本身即可。  如需詳細資訊，請參閱 <xref:System.Printing.PrintQueueStatus>、[& 運算子 \(C\# 參考\)](../Topic/&%20Operator%20\(C%23%20Reference\).md) 和 <xref:System.FlagsAttribute>。  
  
 針對每個已設定位元的屬性，程式碼會在呈現給使用者的最終報告中加入注意事項   \(下面會討論在程式碼結尾呼叫的 **ReportAvailabilityAtThisTime** 方法\)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 若要使用每個屬性檢查印表機狀態，則只需要讀取每個屬性，並將注意事項加入至屬性為 `true` 時呈現給使用者的最終報告   \(下面會討論在程式碼結尾呼叫的 **ReportAvailabilityAtThisTime** 方法\)。  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 如果需要判斷佇列目前是否可用，則可以建立 **ReportAvailabilityAtThisTime** 方法。  
  
 如果 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> 和 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> 屬性相等，則這個方法不會有任何作用，原因是在那種情況下，印表機隨時都可以使用。  如果不同，則這個方法會取得目前時間，接著必須將這個時間轉換為午夜之後的分鐘總數，原因是 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> 和 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> 屬性都是表示午夜之後分鐘總數的 <xref:System.Int32>，而不是 <xref:System.DateTime> 物件。  最後，這個方法會檢查目前時間是否介於開始與「結束」時間之間。  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## 請參閱  
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
 [& 運算子 \(C\# 參考\)](../Topic/&%20Operator%20\(C%23%20Reference\).md)   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)