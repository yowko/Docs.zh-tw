---
title: "如何：驗證和合併 PrintTickets | Microsoft Docs"
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
  - "合併 PrintTickets"
  - "PrintTicket, 合併"
  - "PrintTicket, 驗證"
  - "PrintTickets 驗證"
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：驗證和合併 PrintTickets
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [列印結構描述](http://go.microsoft.com/fwlink/?LinkId=186397)包含靈活可擴充的 <xref:System.Printing.PrintCapabilities> 和 <xref:System.Printing.PrintTicket> 項目。  前者將列印裝置的功能項目化，後者則指定當裝置遇到特定文件系列、個別文件或個別頁面時該如何使用這些功能。  
  
 對於支援列印功能的應用程式來說，一般的工作順序如下。  
  
1.  判斷印表機的功能。  
  
2.  設定要使用這些功能的 <xref:System.Printing.PrintTicket>。  
  
3.  驗證 <xref:System.Printing.PrintTicket>。  
  
 本文章中將說明做法。  
  
## 範例  
 在以下的簡單範例中，我們只對印表機是否支援雙面列印有興趣。  主要的步驟如下。  
  
1.  以 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> 方法取得 <xref:System.Printing.PrintCapabilities> 物件。  
  
2.  測試是否有您想要的功能。  在以下範例中，我們會測試  <xref:System.Printing.PrintCapabilities> 物件的 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> 屬性，找出是否有在同一張紙的正反面列印，同時會在紙張長邊「翻頁」的功能。  因為 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> 是集合，所以我們使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 的 `Contains` 方法。  
  
    > [!NOTE]
    >  這不是絕對必要的步驟。  以下使用的 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> 方法會檢查  <xref:System.Printing.PrintTicket> 中的每個印表機功能要求。  如果印表機不支援要求的功能，印表機驅動程式會在被方法退回的 <xref:System.Printing.PrintTicket> 中將要求替換為別的要求。  
  
3.  如果印表機支援兩面列印，範例程式碼就會建立要求雙面列印的 <xref:System.Printing.PrintTicket>。  但是應用程式不會在  <xref:System.Printing.PrintTicket> 項目中指定每個可能的印表機設定值。  這會浪費程式設計人員和程式的時間。  程式碼只會設定雙面列印要求，然後將這個 <xref:System.Printing.PrintTicket> 與完全設定好且驗證好的現有 <xref:System.Printing.PrintTicket> 合併 \(在這個案例中，就是使用者的預設 <xref:System.Printing.PrintTicket>\)。  
  
4.  因此，範例程式碼呼叫 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> 方法以將新的迷你 <xref:System.Printing.PrintTicket> 與使用者的預設 <xref:System.Printing.PrintTicket> 合併。  這會傳回 <xref:System.Printing.ValidationResult>，它將新的 <xref:System.Printing.PrintTicket> 變為它的屬性之一。  
  
5.  然後範例程式碼測試新的 <xref:System.Printing.PrintTicket> 會不會要求雙面列印。  如果會，範例程式碼會將它變為使用者新的預設列印票證。  如果沒有做上述的步驟 2，且印表機不支援從紙張長邊翻頁的雙面列印，測試結果就是 `false` \(請參閱上述的「注意事項」\)。  
  
6.  最後的重要步驟是以 <xref:System.Printing.PrintQueue.Commit%2A> 方法認可 <xref:System.Printing.PrintQueue> 的 <xref:System.Printing.PrintQueue.UserPrintTicket%2A> 屬性變更。  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 為方便您快速測試這個範例，其餘內容在下面。  請建立專案和命名空間，然後將這篇文章的兩個程式碼片段貼到命名空間區塊中。  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## 請參閱  
 <xref:System.Printing.PrintCapabilities>   
 <xref:System.Printing.PrintTicket>   
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>   
 <xref:System.Printing.PrintServer>   
 <xref:System.Printing.EnumeratedPrintQueueTypes>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>   
 [WPF 中的文件](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [列印概觀](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [列印結構描述](http://go.microsoft.com/fwlink/?LinkId=186397)