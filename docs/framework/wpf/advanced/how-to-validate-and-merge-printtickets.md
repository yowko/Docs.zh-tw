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
ms.openlocfilehash: 15e328729886e0f1efc3b47705fcb4ce13013137
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035580"
---
# <a name="how-to-validate-and-merge-printtickets"></a>如何：驗證和合併 PrintTickets
Microsoft Windows[列印架構](https://go.microsoft.com/fwlink/?LinkId=186397)包含彈性且可擴充的 <xref:System.Printing.PrintCapabilities> 和 <xref:System.Printing.PrintTicket> 元素。 前者會逐項列出列印裝置的功能，後者會指定裝置應如何使用這些功能，以及特定的檔、個別檔或個別頁面的順序。  
  
 支援列印之應用程式的一般工作順序如下所示。  
  
1. 判斷印表機的功能。  
  
2. 設定 <xref:System.Printing.PrintTicket> 以使用這些功能。  
  
3. 驗證 <xref:System.Printing.PrintTicket>。  
  
 本文說明如何執行這項操作。  
  
## <a name="example"></a>範例  
 在下面的簡單範例中，我們只對印表機是否可以支援雙側列印有興趣。 主要步驟如下所示。  
  
1. 取得具有 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> 方法的 <xref:System.Printing.PrintCapabilities> 物件。  
  
2. 測試是否有您想要的功能。 在下面的範例中，我們會測試 <xref:System.Printing.PrintCapabilities> 物件的 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> 屬性，以取得在紙張的雙面列印的功能，以及工作表長邊的「翻頁」。 因為 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> 是集合，所以我們會使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的 `Contains` 方法。  
  
    > [!NOTE]
    > 此步驟並不是絕對必要的。 下面所使用的 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> 方法將會檢查 <xref:System.Printing.PrintTicket> 中的每個要求是否符合印表機的功能。 如果印表機不支援要求的功能，印表機驅動程式會在方法傳回的 <xref:System.Printing.PrintTicket> 中替代替代要求。  
  
3. 如果印表機支援雙工，則範例程式碼會建立一個要求進行雙工的 <xref:System.Printing.PrintTicket>。 但應用程式不會指定 <xref:System.Printing.PrintTicket> 元素中的每個可能印表機設定。 這會浪費程式設計人員和計畫時間。 相反地，程式碼只會設定雙工要求，然後將此 <xref:System.Printing.PrintTicket> 與現有、完整設定和驗證的 <xref:System.Printing.PrintTicket>（在此案例中為使用者的預設 <xref:System.Printing.PrintTicket>）合併。  
  
4. 因此，此範例會呼叫 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> 方法，將新的、最小的 <xref:System.Printing.PrintTicket> 與使用者的預設 <xref:System.Printing.PrintTicket>合併。 這會傳回包含新 <xref:System.Printing.PrintTicket> 做為其其中一個屬性的 <xref:System.Printing.ValidationResult>。  
  
5. 然後，此範例會測試新的 <xref:System.Printing.PrintTicket> 是否要求雙工。 如果有，則範例會使其成為使用者的新預設列印票證。 如果上述步驟2已被省略，而且印表機不支援長時間的雙面處理，則測試會導致 `false`。 （請參閱上面的注意事項）。  
  
6. 最後一個重要步驟是使用 <xref:System.Printing.PrintQueue.Commit%2A> 方法，將變更認可至 <xref:System.Printing.PrintQueue> 的 <xref:System.Printing.PrintQueue.UserPrintTicket%2A> 屬性。  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 如此一來，您就可以快速測試此範例，如下所示。 建立專案和命名空間，然後將本文中的兩個程式碼片段貼入命名空間區塊。  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [WPF 中的文件](documents-in-wpf.md)
- [列印概觀](printing-overview.md)
- [列印架構](https://go.microsoft.com/fwlink/?LinkId=186397)
