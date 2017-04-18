---
title: "如何：得知列印工作是否可在此時列印 | Microsoft Docs"
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
  - "列印工作, 計時"
  - "列印佇列, 計時"
  - "印表機, 可用性"
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：得知列印工作是否可在此時列印
列印佇列並非總是一天 24 小時皆可使用。  它們可能已設定開始與結束時間屬性，以決定一天中無法使用的特定時間。  例如，這項功能可以在下午 5 點後將某部印表機保留給特定部門使用。  該部門會使用不同於其他部門的佇列來提供列印內容給這部印表機。  其他部門的佇列將設為在下午 5 點後無法使用，而這個部門的佇列則設為在任何時間皆可使用。  
  
 此外，列印工作本身也可以設為只能在指定時段內進行列印。  
  
 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 的 [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] 中公開的 <xref:System.Printing.PrintQueue> 與 <xref:System.Printing.PrintSystemJobInfo> 類別，可讓使用者從遠端查看指定的列印工作目前是否可以在指定的佇列上進行列印。  
  
## 範例  
 下列範例是可以診斷列印工作問題的範例。  
  
 這種功能主要有兩項步驟，如下所示。  
  
1.  讀取 <xref:System.Printing.PrintQueue> 的 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> 與 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> 屬性，以判斷目前的時間是否介於這兩者之間。  
  
2.  讀取 <xref:System.Printing.PrintSystemJobInfo> 的 <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> 與 <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> 屬性，以判斷目前的時間是否介於這兩者之間。  
  
 但這些屬性並非 <xref:System.DateTime> 物件，因此情況較為複雜。  這些屬性屬於 <xref:System.Int32> 物件，它們以自午夜後經過的分鐘數來表示一天中的時間。  而且，所謂的午夜並非指目前時區的午夜，而是 UTC \(Coordinated Universal Time\) 的午夜。  
  
 第一個程式碼範例呈現靜態方法 **ReportQueueAndJobAvailability**，這個方法會接收 <xref:System.Printing.PrintSystemJobInfo>，並呼叫 Helper 方法以判斷目前該工作是否可進行列印，如果不行，則何時可列印。  請注意，這個方法接收的不是 <xref:System.Printing.PrintQueue>。  這是因為 <xref:System.Printing.PrintSystemJobInfo> 的 <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> 屬性中已包含這個佇列的參考。  
  
 從屬方法包括多載的 **ReportAvailabilityAtThisTime** 方法，這個方法可以採用 <xref:System.Printing.PrintQueue> 或 <xref:System.Printing.PrintSystemJobInfo> 做為參數。  此外還有 **TimeConverter.ConvertToLocalHumanReadableTime**。  這些方法都將在稍後討論。  
  
 **ReportQueueAndJobAvailability** 首先會檢查佇列或列印工作目前是否無法使用。  如有其中之一無法使用，它就會檢查佇列是否無法使用。  如果佇列無法使用，這個方法即會回報這個事實以及佇列何時可以恢復使用。  接著這個方法會檢查工作，如果工作無法使用，則會回報這個工作下次可進行列印的時段。  最後，這個方法會回報工作最快可以進行列印的時間。  這個時間為下列兩個時間中較晚發生者。  
  
-   列印佇列下次可用的時間。  
  
-   列印工作下次可用的時間。  
  
 當報告一天中的時間時，也會呼叫 <xref:System.DateTime.ToShortTimeString%2A> 方法，因為這個方法會在輸出中隱藏年、月與日。  您無法限制列印佇列或列印工作在特定年、月或日的可用性。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 **ReportAvailabilityAtThisTime** 方法的兩個多載除了接收的型別不同，其他方面都是相同的，因此下方僅呈現 <xref:System.Printing.PrintQueue> 的版本  
  
> [!NOTE]
>  這裡引發了一個問題：既然這兩個方法除了型別以外其他方面皆相同，為何這個範例不直接建立泛型的 **ReportAvailabilityAtThisTime\<T\>** 方法？  原因在於這類方法的類別必須限制為具有該方法所呼叫之 **StartTimeOfDay** 與 **UntilTimeOfDay** 屬性的類別，但泛型方法只能限制為單一類別，以及繼承樹狀目錄中，不具這類屬性的 <xref:System.Printing.PrintSystemObject> 之 <xref:System.Printing.PrintQueue> 與 <xref:System.Printing.PrintSystemJobInfo> 的唯一共通類別。  
  
 **ReportAvailabilityAtThisTime** 方法 \(如下列程式碼範例所示\) 首先會將 <xref:System.Boolean> Sentinel 變數初始化為 `true`。  如果佇列無法使用則會重設為 `false`。  
  
 接著，這個方法會檢查開始與結束 \(Until\) 時間是否相同。  如果相同則表示佇列一律可用，而這個方法會傳回 `true`。  
  
 如果佇列並非隨時可用，這個方法會使用靜態 <xref:System.DateTime.UtcNow%2A> 屬性取得目前的時間以做為 <xref:System.DateTime> 物件   \(並不需要本地時間，因為 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> 與 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> 屬性本身皆使用 UTC 時間\)。  
  
 但這兩個屬性並非 <xref:System.DateTime> 物件。  它們是 <xref:System.Int32>，會以自 UTC 午夜後經過的分鐘數來表示一天中的時間。  因此我們必須將 <xref:System.DateTime> 物件轉換成午夜後經過的分鐘數。  完成這個動作後，這個方法會直接檢查目前的時間 \(Now\) 是否介於佇列的開始與結束 \(Until\) 時間之間，若否則將 Sentinel 設為 false，並傳回 Sentinel。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime** 方法 \(如下列程式碼範例所示\) 不會使用 [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] 所提供的方法，因此在這裡僅略加討論。  這個方法具有雙重轉換工作：它必須取得表示午夜後所經過分鐘數的整數，再將其轉換為一般人可讀取的時間，而且必須轉換為本地時間。  它會先建立設為午夜 UTC 的 <xref:System.DateTime> 物件，再使用 <xref:System.DateTime.AddMinutes%2A> 方法加上這個方法接收的分鐘數，藉以完成上述動作。  這樣會傳回新的 <xref:System.DateTime>，表示這個方法收的原始時間。  接著，<xref:System.DateTime.ToLocalTime%2A> 方法就會將這個時間轉換成本地時間。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## 請參閱  
 <xref:System.DateTime>   
 <xref:System.Printing.PrintSystemJobInfo>   
 <xref:System.Printing.PrintQueue>   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)