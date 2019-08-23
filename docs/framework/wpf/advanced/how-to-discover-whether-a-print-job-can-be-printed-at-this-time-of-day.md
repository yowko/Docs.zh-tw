---
title: 作法：得知每天此時可否列印列印工作
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
ms.openlocfilehash: 859dc75169e443d07361951692a428507886fa2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947803"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>HOW TO：得知每天此時可否列印列印工作
列印佇列一天不一定會有24小時的時間。 它們具有可設定的開始和結束時間屬性, 使其在一天的特定時間無法使用。 例如, 您可以使用這項功能來保留印表機, 以在下午5點之後專門用於特定部門。 該部門會有與其他部門所使用的印表機不同的佇列服務。 其他部門的佇列會在下午5點後設定為無法使用, 而適用部門的佇列則可以設定為隨時可用。  
  
 此外, 列印工作本身只能在指定的一段時間內設定為可列印。  
  
 Microsoft <xref:System.Printing.PrintQueue> .NET Framework <xref:System.Printing.PrintSystemJobInfo>的 api 中公開的和類別, 可讓您從遠端檢查給定的列印工作是否可以在目前的佇列中列印。  
  
## <a name="example"></a>範例  
 以下範例是可以診斷列印工作問題的範例。  
  
 這類函數有兩個主要步驟, 如下所示。  
  
1. 請參閱的<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> <xref:System.Printing.PrintQueue>和屬性, 以判斷目前的時間是否介於兩者之間。 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
  
2. 請參閱的<xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> <xref:System.Printing.PrintSystemJobInfo>和屬性, 以判斷目前的時間是否介於兩者之間。 <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>  
  
 但是複雜性是因為這些屬性不<xref:System.DateTime>是物件。 相反地, <xref:System.Int32>它們是以午夜開始的分鐘數表示的物件。 此外, 這不是目前時區的午夜, 而是 UTC 午夜 (國際標準時間)。  
  
 第一個程式碼範例會呈現靜態方法**ReportQueueAndJobAvailability**, 它會傳遞<xref:System.Printing.PrintSystemJobInfo>並呼叫 helper 方法, 以判斷作業是否可以在目前的時間列印, 如果沒有的話, 可以列印。 請注意, <xref:System.Printing.PrintQueue>不會傳遞至方法。 這是因為在<xref:System.Printing.PrintSystemJobInfo>其<xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>屬性中包含佇列的參考。  
  
 從屬方法包含多載的**ReportAvailabilityAtThisTime**方法, 可以接受<xref:System.Printing.PrintQueue>或<xref:System.Printing.PrintSystemJobInfo>做為參數。 另外還有一個**TimeConverter。 ConvertToLocalHumanReadableTime**。 以下將討論所有這些方法。  
  
 **ReportQueueAndJobAvailability**方法一開始會先查看佇列或列印工作是否無法使用。 如果其中一個無法使用, 則會檢查佇列是否無法使用。 如果無法使用, 則方法會回報此事實以及佇列再次可用的時間。 然後, 它會檢查工作, 如果無法使用, 它會報告下一個時間範圍 (當它可以列印時)。 最後, 方法會報告作業可以列印的最早時間。 這是下列兩次的後續動作。  
  
- 列印佇列下次可用的時間。  
  
- 列印工作下一次可用的時間。  
  
 當報告一天的時間時<xref:System.DateTime.ToShortTimeString%2A> , 也會呼叫方法, 因為這個方法會抑制輸出中的年、月和日。 您無法將列印佇列或列印工作的可用性限制為特定年、月或日。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 **ReportAvailabilityAtThisTime**方法的兩個多載與傳遞給它們的型別相同, 但只有版本才<xref:System.Printing.PrintQueue>會顯示在下方。  
  
> [!NOTE]
> 除了 type 以外, 方法會引發為什麼範例不會建立 **\<ReportAvailabilityAtThisTime T >** 泛型方法的問題。 原因是, 這類方法必須限制為具有方法所呼叫之**StartTimeOfDay**和**system.printing.printqueue.untiltimeofday**屬性的類別, 但泛型方法只能限制為單一類別, 而且兩者都通用的唯一類別而在繼承樹狀結構<xref:System.Printing.PrintSystemJobInfo> 中,沒有這類屬性。<xref:System.Printing.PrintSystemObject> <xref:System.Printing.PrintQueue>  
  
 **ReportAvailabilityAtThisTime**方法 (在下面的程式碼範例中提供) 一開始會<xref:System.Boolean>將 sentinel 變數`true`初始化為。 如果佇列無法使用, `false`則會重設為。  
  
 接下來, 方法會檢查開始和 "until" 時間是否相同。 如果是, 則佇列一律可供使用, 因此方法`true`會傳回。  
  
 如果佇列在所有時間都無法使用, 方法會使用靜態<xref:System.DateTime.UtcNow%2A>屬性來取得目前的時間<xref:System.DateTime>做為物件。 (我們不需要當地時間<xref:System.Printing.PrintQueue.StartTimeOfDay%2A> , 因為和<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>屬性本身都是 UTC 時間)。  
  
 不過, 這兩個屬性不<xref:System.DateTime>是物件。 它們會<xref:System.Int32>將時程表示為分鐘數-UTC 後午夜。 因此, 我們必須將<xref:System.DateTime>物件轉換為午夜之後的分鐘數。 完成此動作時, 方法只會檢查 "now" 是否介於佇列的開始和 "until" 時間之間, 如果 "now" 不在兩個時間之間, 則會將 sentinel 設定為 false, 並傳回 sentinel。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter. ConvertToLocalHumanReadableTime**方法 (在下面的程式碼範例中提供) 不會使用 Microsoft .NET Framework 所引進的任何方法, 因此, 討論內容很簡單。 方法具有雙重轉換工作: 它必須採用整數, 表示分鐘-午夜後, 並將它轉換成人們可讀取的時間, 而且必須將此轉換成當地時間。 完成這項工作的方法是<xref:System.DateTime>先建立一個設定為午夜 UTC 的物件, 然後<xref:System.DateTime.AddMinutes%2A>使用方法來加入傳遞至方法的分鐘數。 這會傳回新<xref:System.DateTime>的, 表示傳遞至方法的原始時間。 然後<xref:System.DateTime.ToLocalTime%2A> , 方法會將此轉換成當地時間。  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
