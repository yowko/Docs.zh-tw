---
title: 如何：驗證和合併 PrintTickets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: 37a1c0600b8429158336968507ddc8cfb6d8f98b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485634"
---
# <a name="how-to-validate-and-merge-printtickets"></a>如何：驗證和合併 PrintTickets
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [列印結構描述](https://go.microsoft.com/fwlink/?LinkId=186397)包括有彈性且可延伸<xref:System.Printing.PrintCapabilities>和<xref:System.Printing.PrintTicket>項目。 前者的逐項列出列印裝置的功能，後者則指定裝置應該如何使用這些功能對於特定的一連串的文件、 個別的文件或個別的頁面。  
  
 一般的應用程式可支援列印的工作順序會如下所示。  
  
1.  判斷印表機的功能。  
  
2.  設定<xref:System.Printing.PrintTicket>才能使用這些功能。  
  
3.  驗證<xref:System.Printing.PrintTicket>。  
  
 這篇文章會示範如何執行這項操作。  
  
## <a name="example"></a>範例  
 在下列簡單範例中，我們只是要確定印表機是否可以支援雙面列印 — 雙面列印。 主要步驟如下所示。  
  
1.  取得<xref:System.Printing.PrintCapabilities>物件<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>方法。  
  
2.  測試有您想要的功能。 在下列範例中，我們測試<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>屬性<xref:System.Printing.PrintCapabilities>沿著長的側邊，工作表的物件是否存在，列印一張紙 」 頁面開啟 「 紙張的雙面的功能。 由於<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>是一個集合中，我們會使用`Contains`方法<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>。  
  
    > [!NOTE]
    >  此步驟並非絕對必要。 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>以下使用的方法會檢查每個要求<xref:System.Printing.PrintTicket>印表機的功能。 如果印表機不支援所要求的功能，印表機驅動程式將會替代中的替代要求<xref:System.Printing.PrintTicket>方法所傳回。  
  
3.  如果印表機支援雙面列印，範例程式碼會建立<xref:System.Printing.PrintTicket>雙工的要求。 但應用程式不會指定每個設定中可用的印表機可能<xref:System.Printing.PrintTicket>項目。 這會浪費的程式設計人員和程式的時間。 相反地，程式碼設定雙面列印要求，然後合併這<xref:System.Printing.PrintTicket>與現有，完整設定及驗證過<xref:System.Printing.PrintTicket>，在此案例中，使用者的預設<xref:System.Printing.PrintTicket>。  
  
4.  因此，此範例會呼叫<xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>方法來合併新的最少，<xref:System.Printing.PrintTicket>使用者的預設值<xref:System.Printing.PrintTicket>。 這會傳回<xref:System.Printing.ValidationResult>，其中包含新<xref:System.Printing.PrintTicket>為其中一個屬性。  
  
5.  然後此範例會測試的新<xref:System.Printing.PrintTicket>要求雙面列印。 若是如此，然後此範例可讓使用者新的預設列印票證。 如果上述步驟 2 已省略，而且印表機不支援雙工沿著長的側邊，則測試可能會導致`false`。 （請參閱上面的附註）。  
  
6.  最後一個重要步驟是將認可的變更<xref:System.Printing.PrintQueue.UserPrintTicket%2A>的屬性<xref:System.Printing.PrintQueue>與<xref:System.Printing.PrintQueue.Commit%2A>方法。  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 因此，您可以快速測試此範例中，它的其餘部分將顯示如下。 建立專案和命名空間，然後在這篇文章中的兩個程式碼片段貼到命名空間區塊。  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [列印結構描述](https://go.microsoft.com/fwlink/?LinkId=186397)
