---
title: HOW TO：驗證和合併 PrintTickets
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
ms.openlocfilehash: 2be08f5d3c2cd82e50569a105e3fa15f12ad352c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355164"
---
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="be1b8-102">HOW TO：驗證和合併 PrintTickets</span><span class="sxs-lookup"><span data-stu-id="be1b8-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="be1b8-103">[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [列印結構描述](https://go.microsoft.com/fwlink/?LinkId=186397)包括有彈性且可延伸<xref:System.Printing.PrintCapabilities>和<xref:System.Printing.PrintTicket>項目。</span><span class="sxs-lookup"><span data-stu-id="be1b8-103">The [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="be1b8-104">前者的逐項列出列印裝置的功能，後者則指定裝置應該如何使用這些功能對於特定的一連串的文件、 個別的文件或個別的頁面。</span><span class="sxs-lookup"><span data-stu-id="be1b8-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="be1b8-105">一般的應用程式可支援列印的工作順序會如下所示。</span><span class="sxs-lookup"><span data-stu-id="be1b8-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1.  <span data-ttu-id="be1b8-106">判斷印表機的功能。</span><span class="sxs-lookup"><span data-stu-id="be1b8-106">Determine a printer's capabilities.</span></span>  
  
2.  <span data-ttu-id="be1b8-107">設定<xref:System.Printing.PrintTicket>才能使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="be1b8-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3.  <span data-ttu-id="be1b8-108">驗證<xref:System.Printing.PrintTicket>。</span><span class="sxs-lookup"><span data-stu-id="be1b8-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="be1b8-109">這篇文章會示範如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="be1b8-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be1b8-110">範例</span><span class="sxs-lookup"><span data-stu-id="be1b8-110">Example</span></span>  
 <span data-ttu-id="be1b8-111">在下列簡單範例中，我們只是要確定印表機是否可以支援雙面列印 — 雙面列印。</span><span class="sxs-lookup"><span data-stu-id="be1b8-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="be1b8-112">主要步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="be1b8-112">The major steps are as follows.</span></span>  
  
1.  <span data-ttu-id="be1b8-113">取得<xref:System.Printing.PrintCapabilities>物件<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="be1b8-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2.  <span data-ttu-id="be1b8-114">測試有您想要的功能。</span><span class="sxs-lookup"><span data-stu-id="be1b8-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="be1b8-115">在下列範例中，我們測試<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>屬性<xref:System.Printing.PrintCapabilities>沿著長的側邊，工作表的物件是否存在，列印一張紙 」 頁面開啟 「 紙張的雙面的功能。</span><span class="sxs-lookup"><span data-stu-id="be1b8-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="be1b8-116">由於<xref:System.Printing.PrintCapabilities.DuplexingCapability%2A>是一個集合中，我們會使用`Contains`方法<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>。</span><span class="sxs-lookup"><span data-stu-id="be1b8-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be1b8-117">此步驟並非絕對必要。</span><span class="sxs-lookup"><span data-stu-id="be1b8-117">This step is not strictly necessary.</span></span> <span data-ttu-id="be1b8-118"><xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>以下使用的方法會檢查每個要求<xref:System.Printing.PrintTicket>印表機的功能。</span><span class="sxs-lookup"><span data-stu-id="be1b8-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="be1b8-119">如果印表機不支援所要求的功能，印表機驅動程式將會替代中的替代要求<xref:System.Printing.PrintTicket>方法所傳回。</span><span class="sxs-lookup"><span data-stu-id="be1b8-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3.  <span data-ttu-id="be1b8-120">如果印表機支援雙面列印，範例程式碼會建立<xref:System.Printing.PrintTicket>雙工的要求。</span><span class="sxs-lookup"><span data-stu-id="be1b8-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="be1b8-121">但應用程式不會指定每個設定中可用的印表機可能<xref:System.Printing.PrintTicket>項目。</span><span class="sxs-lookup"><span data-stu-id="be1b8-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="be1b8-122">這會浪費的程式設計人員和程式的時間。</span><span class="sxs-lookup"><span data-stu-id="be1b8-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="be1b8-123">相反地，程式碼設定雙面列印要求，然後合併這<xref:System.Printing.PrintTicket>與現有，完整設定及驗證過<xref:System.Printing.PrintTicket>，在此案例中，使用者的預設<xref:System.Printing.PrintTicket>。</span><span class="sxs-lookup"><span data-stu-id="be1b8-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4.  <span data-ttu-id="be1b8-124">因此，此範例會呼叫<xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A>方法來合併新的最少，<xref:System.Printing.PrintTicket>使用者的預設值<xref:System.Printing.PrintTicket>。</span><span class="sxs-lookup"><span data-stu-id="be1b8-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="be1b8-125">這會傳回<xref:System.Printing.ValidationResult>，其中包含新<xref:System.Printing.PrintTicket>為其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="be1b8-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5.  <span data-ttu-id="be1b8-126">然後此範例會測試的新<xref:System.Printing.PrintTicket>要求雙面列印。</span><span class="sxs-lookup"><span data-stu-id="be1b8-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="be1b8-127">若是如此，然後此範例可讓使用者新的預設列印票證。</span><span class="sxs-lookup"><span data-stu-id="be1b8-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="be1b8-128">如果上述步驟 2 已省略，而且印表機不支援雙工沿著長的側邊，則測試可能會導致`false`。</span><span class="sxs-lookup"><span data-stu-id="be1b8-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="be1b8-129">（請參閱上面的附註）。</span><span class="sxs-lookup"><span data-stu-id="be1b8-129">(See the note above.)</span></span>  
  
6.  <span data-ttu-id="be1b8-130">最後一個重要步驟是將認可的變更<xref:System.Printing.PrintQueue.UserPrintTicket%2A>的屬性<xref:System.Printing.PrintQueue>與<xref:System.Printing.PrintQueue.Commit%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="be1b8-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="be1b8-131">因此，您可以快速測試此範例中，它的其餘部分將顯示如下。</span><span class="sxs-lookup"><span data-stu-id="be1b8-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="be1b8-132">建立專案和命名空間，然後在這篇文章中的兩個程式碼片段貼到命名空間區塊。</span><span class="sxs-lookup"><span data-stu-id="be1b8-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="be1b8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be1b8-133">See also</span></span>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="be1b8-134">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="be1b8-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="be1b8-135">列印概觀</span><span class="sxs-lookup"><span data-stu-id="be1b8-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="be1b8-136">列印結構描述</span><span class="sxs-lookup"><span data-stu-id="be1b8-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
