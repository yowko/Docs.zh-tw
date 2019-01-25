---
title: HOW TO：得知列印工作是否可在此時列印
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: 2abb9939917d4fc10a345b6199e2eb67054bf0c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676688"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>HOW TO：得知列印工作是否可在此時列印
列印佇列並不一定可為一天 24 小時。 還可以設定讓它們無法使用在一天的特定時間的開始和結束時間屬性。 這項功能可用，例如，保留獨佔使用的特定部門下午 5 點後的印表機。 該部門會有不同的佇列服務的印表機，比其他部門使用。 其他部門的佇列會被設定為無法使用下午 5 點後，而佇列為偏好的部門可能被設定為隨時可供使用。  
  
 此外，列印工作本身也可以設定為只在指定的時間範圍內的可列印。  
  
 <xref:System.Printing.PrintQueue>並<xref:System.Printing.PrintSystemJobInfo>類別中公開[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]Microsoft.NET framework 提供的方法從遠端檢查目前是否可以有指定的列印工作列印指定的佇列上。  
  
## <a name="example"></a>範例  
 下列範例是可以診斷問題列印工作的範例。  
  
 發生這種函式的兩個主要步驟如下所示。  
  
1.  讀取<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>並<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>的屬性<xref:System.Printing.PrintQueue>來判斷目前的時間兩者之間。  
  
2.  讀取<xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>並<xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A>的屬性<xref:System.Printing.PrintSystemJobInfo>來判斷目前的時間兩者之間。  
  
 但很複雜的情況起因於這些屬性不是<xref:System.DateTime>物件。 而是<xref:System.Int32>express 一天的時間為午夜起的分鐘數的物件。 此外，這不是午夜中目前的時區，但午夜 UTC （國際標準時間）。  
  
 第一個程式碼範例顯示的靜態方法**ReportQueueAndJobAvailability**，傳遞<xref:System.Printing.PrintSystemJobInfo>呼叫 helper 方法來判斷工作是否可以列印在目前的時間，而如果不是，當它可以列印。 請注意，<xref:System.Printing.PrintQueue>不會傳遞給方法。 這是因為<xref:System.Printing.PrintSystemJobInfo>包含佇列中的參考其<xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>屬性。  
  
 從屬的方法包括多載**ReportAvailabilityAtThisTime**方法可接受下列<xref:System.Printing.PrintQueue>或<xref:System.Printing.PrintSystemJobInfo>做為參數。 另外還有**TimeConverter.ConvertToLocalHumanReadableTime**。 下面會討論所有這些方法。  
  
 **ReportQueueAndJobAvailability**方法一開始會檢查是否有佇列或列印工作無法使用這一次。 如果其中任一無法使用，接著它會檢查是否無法使用的佇列。 如果無法使用，方法會報告此事實和佇列何時會提供一次的時間。 接著它會檢查作業和無法使用時，它會報告的下一個時間範圍時它可進行列印。 最後，方法會報告工作可以列印時的最早時間。 這是遵循兩次的更新版本。  
  
-   列印佇列下一個可用的時間。  
  
-   列印工作下一個可用的時間。  
  
 報告時間的日、 時<xref:System.DateTime.ToShortTimeString%2A>因為這個方法會隱藏，年、 月和日從輸出中，也會呼叫方法。 您無法限制列印佇列或列印工作的可用性以特定的年、 月或日。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 兩個多載**ReportAvailabilityAtThisTime**方法除了之外完全相同的型別傳遞給它們，因此只有<xref:System.Printing.PrintQueue>版本顯示如下。  
  
> [!NOTE]
>  方法是相同型別除外，這會引發的問題，此範例不會建立泛型方法的原因**ReportAvailabilityAtThisTime\<T >**。 原因是這種方法必須具有的類別只能**StartTimeOfDay**並**UntilTimeOfDay**只能限制為屬性的方法呼叫，但泛型方法單一類別和唯一類別同時<xref:System.Printing.PrintQueue>並<xref:System.Printing.PrintSystemJobInfo>在繼承樹狀結構是<xref:System.Printing.PrintSystemObject>具有任何這類屬性。  
  
 **ReportAvailabilityAtThisTime** （如下列程式碼範例所示） 的方法一開始會初始化<xref:System.Boolean>sentinel 變數`true`。 它會重設為`false`，如果不是可用的佇列。  
  
 接下來，此方法會檢查是否要啟動 「 直到 」 時間完全相同。 如有需要，佇列已一律使用，所以此方法會傳回`true`。  
  
 如果佇列不是可用的時間，此方法會使用靜態<xref:System.DateTime.UtcNow%2A>屬性，以取得目前的時間，<xref:System.DateTime>物件。 (我們不需要本地時間因為<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性本身都是以 UTC 時間。)  
  
 不過，這兩個屬性都不<xref:System.DateTime>物件。 它們是<xref:System.Int32>做為午夜之後 UTC 分鐘數表示時間的 s。 我們也需要將我們<xref:System.DateTime>物件在午夜後分鐘的時間。 完成時，方法只會檢查以查看是否 「 現在 」 為佇列的開始之間，以及 「 直到 」 時間，設定為 false，如果 「 現在 」 sentinel 不是介於兩次，並傳回 sentinel。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime**方法 （如下列程式碼範例所示） 不會使用所導入的 Microsoft.NET Framework，因此討論是簡短的任何方法。 方法具有雙重轉換工作： 它必須採用整數，表示在午夜後分鐘的時間，並將它轉換為人們可讀取的時間，它必須將其轉換成當地時間。 其達成方式是先建立<xref:System.DateTime>物件，會設定為 UTC，然後它會使用的午夜<xref:System.DateTime.AddMinutes%2A>將跟著傳遞至此方法的分鐘數的方法。 這會傳回新<xref:System.DateTime>表示傳遞至方法的原始時間。 <xref:System.DateTime.ToLocalTime%2A>方法接著會將此轉換當地時間。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)
