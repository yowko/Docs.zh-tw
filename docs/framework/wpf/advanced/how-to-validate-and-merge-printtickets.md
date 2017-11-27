---
title: "如何：驗證和合併 PrintTickets"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a2c2929f37895f0dee5529a5bf90f84146585032
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="f5c4e-102">如何：驗證和合併 PrintTickets</span><span class="sxs-lookup"><span data-stu-id="f5c4e-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="f5c4e-103">[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [列印結構描述](http://go.microsoft.com/fwlink/?LinkId=186397)包含彈性和可延伸<xref:System.Printing.PrintCapabilities>和<xref:System.Printing.PrintTicket>項目。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](http://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="f5c4e-104">前者逐項列出的列印裝置的功能，後者會指定如何裝置應該使用那些功能相對於特定的一連串的文件、 個別的文件或個別頁面。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="f5c4e-105">一般的支援列印的應用程式的工作順序將會如下所示。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1.  <span data-ttu-id="f5c4e-106">判斷印表機的功能。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-106">Determine a printer's capabilities.</span></span>  
  
2.  <span data-ttu-id="f5c4e-107">設定<xref:System.Printing.PrintTicket>使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3.  <span data-ttu-id="f5c4e-108">驗證<xref:System.Printing.PrintTicket>。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="f5c4e-109">這篇文章會示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5c4e-110">範例</span><span class="sxs-lookup"><span data-stu-id="f5c4e-110">Example</span></span>  
 <span data-ttu-id="f5c4e-111">在下列簡單範例中，我們只是要確定印表機是否可以支援雙工 — 雙面列印。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="f5c4e-112">主要步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-112">The major steps are as follows.</span></span>  
  
1.  <span data-ttu-id="f5c4e-113">取得<xref:System.Printing.PrintCapabilities>物件<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2.  <span data-ttu-id="f5c4e-114">測試有您想要的功能。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="f5c4e-115">在下列範例中，我們測試<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>屬性<xref:System.Printing.PrintCapabilities>物件是否存在張紙 」 頁面開啟 「 雙面列印功能的工作表的長邊。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="f5c4e-116">因為<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>是集合，我們使用`Contains`方法<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f5c4e-117">這個步驟不是絕對必要的。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-117">This step is not strictly necessary.</span></span> <span data-ttu-id="f5c4e-118"><xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>使用下列方法會檢查每個要求<xref:System.Printing.PrintTicket>針對印表機的功能。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="f5c4e-119">如果要求的功能不支援的印表機，印表機驅動程式將會替代的替代要求中<xref:System.Printing.PrintTicket>方法所傳回。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3.  <span data-ttu-id="f5c4e-120">如果印表機支援雙面列印，範例程式碼會建立<xref:System.Printing.PrintTicket>雙工的要求。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="f5c4e-121">但應用程式不會指定每個設定中可用的印表機可能會發生<xref:System.Printing.PrintTicket>項目。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="f5c4e-122">這會浪費的程式設計人員和程式的時間。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="f5c4e-123">相反地，此程式碼設定雙工要求，並接著將合併這<xref:System.Printing.PrintTicket>與現有的完整設定及驗證過<xref:System.Printing.PrintTicket>，在此情況下，使用者的預設<xref:System.Printing.PrintTicket>。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4.  <span data-ttu-id="f5c4e-124">因此，範例會呼叫<xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>方法，將新的合併至最小，<xref:System.Printing.PrintTicket>使用者的預設值<xref:System.Printing.PrintTicket>。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="f5c4e-125">這會傳回<xref:System.Printing.ValidationResult>，其中包含新<xref:System.Printing.PrintTicket>做為其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5.  <span data-ttu-id="f5c4e-126">然後此範例會測試的新<xref:System.Printing.PrintTicket>要求雙面列印。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="f5c4e-127">若是如此，然後此範例可讓使用者新的預設列印票證。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="f5c4e-128">如果上述步驟 2 已遺漏，而且印表機不支援長邊雙面列印則測試可能會導致`false`。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="f5c4e-129">（請參閱上面的附註）。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-129">(See the note above.)</span></span>  
  
6.  <span data-ttu-id="f5c4e-130">最後的重要步驟是以認可變更到<xref:System.Printing.PrintQueue.UserPrintTicket%2A>屬性<xref:System.Printing.PrintQueue>與<xref:System.Printing.PrintQueue.Commit%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="f5c4e-131">讓您可以快速測試此範例中，它的其餘部分會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="f5c4e-132">建立專案和命名空間，然後貼入程式碼片段在本文中的命名空間區塊。</span><span class="sxs-lookup"><span data-stu-id="f5c4e-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="f5c4e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5c4e-133">See Also</span></span>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [<span data-ttu-id="f5c4e-134">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="f5c4e-134">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="f5c4e-135">列印概觀</span><span class="sxs-lookup"><span data-stu-id="f5c4e-135">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="f5c4e-136">列印結構描述</span><span class="sxs-lookup"><span data-stu-id="f5c4e-136">Print Schema</span></span>](http://go.microsoft.com/fwlink/?LinkId=186397)
