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
# <a name="how-to-validate-and-merge-printtickets"></a><span data-ttu-id="e822d-102">如何：驗證和合併 PrintTickets</span><span class="sxs-lookup"><span data-stu-id="e822d-102">How to: Validate and Merge PrintTickets</span></span>
<span data-ttu-id="e822d-103">Microsoft Windows[列印架構](https://go.microsoft.com/fwlink/?LinkId=186397)包含彈性且可擴充的 <xref:System.Printing.PrintCapabilities> 和 <xref:System.Printing.PrintTicket> 元素。</span><span class="sxs-lookup"><span data-stu-id="e822d-103">The Microsoft Windows [Print Schema](https://go.microsoft.com/fwlink/?LinkId=186397) includes the flexible and extensible <xref:System.Printing.PrintCapabilities> and <xref:System.Printing.PrintTicket> elements.</span></span> <span data-ttu-id="e822d-104">前者會逐項列出列印裝置的功能，後者會指定裝置應如何使用這些功能，以及特定的檔、個別檔或個別頁面的順序。</span><span class="sxs-lookup"><span data-stu-id="e822d-104">The former itemizes the capabilities of a print device and the latter specifies how the device should use those capabilities with respect to a particular sequence of documents, individual document, or individual page.</span></span>  
  
 <span data-ttu-id="e822d-105">支援列印之應用程式的一般工作順序如下所示。</span><span class="sxs-lookup"><span data-stu-id="e822d-105">A typical sequence of tasks for an application that supports printing would be as follows.</span></span>  
  
1. <span data-ttu-id="e822d-106">判斷印表機的功能。</span><span class="sxs-lookup"><span data-stu-id="e822d-106">Determine a printer's capabilities.</span></span>  
  
2. <span data-ttu-id="e822d-107">設定 <xref:System.Printing.PrintTicket> 以使用這些功能。</span><span class="sxs-lookup"><span data-stu-id="e822d-107">Configure a <xref:System.Printing.PrintTicket> to use those capabilities.</span></span>  
  
3. <span data-ttu-id="e822d-108">驗證 <xref:System.Printing.PrintTicket>。</span><span class="sxs-lookup"><span data-stu-id="e822d-108">Validate the <xref:System.Printing.PrintTicket>.</span></span>  
  
 <span data-ttu-id="e822d-109">本文說明如何執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="e822d-109">This article shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e822d-110">範例</span><span class="sxs-lookup"><span data-stu-id="e822d-110">Example</span></span>  
 <span data-ttu-id="e822d-111">在下面的簡單範例中，我們只對印表機是否可以支援雙側列印有興趣。</span><span class="sxs-lookup"><span data-stu-id="e822d-111">In the simple example below, we are interested only in whether a printer can support duplexing — two-sided printing.</span></span> <span data-ttu-id="e822d-112">主要步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="e822d-112">The major steps are as follows.</span></span>  
  
1. <span data-ttu-id="e822d-113">取得具有 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> 方法的 <xref:System.Printing.PrintCapabilities> 物件。</span><span class="sxs-lookup"><span data-stu-id="e822d-113">Get a <xref:System.Printing.PrintCapabilities> object with the <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> method.</span></span>  
  
2. <span data-ttu-id="e822d-114">測試是否有您想要的功能。</span><span class="sxs-lookup"><span data-stu-id="e822d-114">Test for the presence of the capability you want.</span></span> <span data-ttu-id="e822d-115">在下面的範例中，我們會測試 <xref:System.Printing.PrintCapabilities> 物件的 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> 屬性，以取得在紙張的雙面列印的功能，以及工作表長邊的「翻頁」。</span><span class="sxs-lookup"><span data-stu-id="e822d-115">In the example below, we test the <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> property of the <xref:System.Printing.PrintCapabilities> object for the presence of the capability of printing on both sides of a sheet of paper with the "page turning" along the long side of the sheet.</span></span> <span data-ttu-id="e822d-116">因為 <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> 是集合，所以我們會使用 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的 `Contains` 方法。</span><span class="sxs-lookup"><span data-stu-id="e822d-116">Since <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> is a collection, we use the `Contains` method of <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e822d-117">此步驟並不是絕對必要的。</span><span class="sxs-lookup"><span data-stu-id="e822d-117">This step is not strictly necessary.</span></span> <span data-ttu-id="e822d-118">下面所使用的 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> 方法將會檢查 <xref:System.Printing.PrintTicket> 中的每個要求是否符合印表機的功能。</span><span class="sxs-lookup"><span data-stu-id="e822d-118">The <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method used below will check each request in the <xref:System.Printing.PrintTicket> against the capabilities of the printer.</span></span> <span data-ttu-id="e822d-119">如果印表機不支援要求的功能，印表機驅動程式會在方法傳回的 <xref:System.Printing.PrintTicket> 中替代替代要求。</span><span class="sxs-lookup"><span data-stu-id="e822d-119">If the requested capability is not supported by printer, the printer driver will substitute an alternative request in the <xref:System.Printing.PrintTicket> returned by the method.</span></span>  
  
3. <span data-ttu-id="e822d-120">如果印表機支援雙工，則範例程式碼會建立一個要求進行雙工的 <xref:System.Printing.PrintTicket>。</span><span class="sxs-lookup"><span data-stu-id="e822d-120">If the printer supports duplexing, the sample code creates a <xref:System.Printing.PrintTicket> that asks for duplexing.</span></span> <span data-ttu-id="e822d-121">但應用程式不會指定 <xref:System.Printing.PrintTicket> 元素中的每個可能印表機設定。</span><span class="sxs-lookup"><span data-stu-id="e822d-121">But the application does not specify every possible printer setting available in the <xref:System.Printing.PrintTicket> element.</span></span> <span data-ttu-id="e822d-122">這會浪費程式設計人員和計畫時間。</span><span class="sxs-lookup"><span data-stu-id="e822d-122">That would be wasteful of both programmer and program time.</span></span> <span data-ttu-id="e822d-123">相反地，程式碼只會設定雙工要求，然後將此 <xref:System.Printing.PrintTicket> 與現有、完整設定和驗證的 <xref:System.Printing.PrintTicket>（在此案例中為使用者的預設 <xref:System.Printing.PrintTicket>）合併。</span><span class="sxs-lookup"><span data-stu-id="e822d-123">Instead, the code sets only the duplexing request and then merges this <xref:System.Printing.PrintTicket> with an existing, fully configured and validated, <xref:System.Printing.PrintTicket>, in this case, the user's default <xref:System.Printing.PrintTicket>.</span></span>  
  
4. <span data-ttu-id="e822d-124">因此，此範例會呼叫 <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> 方法，將新的、最小的 <xref:System.Printing.PrintTicket> 與使用者的預設 <xref:System.Printing.PrintTicket>合併。</span><span class="sxs-lookup"><span data-stu-id="e822d-124">Accordingly, the sample calls the <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> method to merge the new, minimal, <xref:System.Printing.PrintTicket> with the user's default <xref:System.Printing.PrintTicket>.</span></span> <span data-ttu-id="e822d-125">這會傳回包含新 <xref:System.Printing.PrintTicket> 做為其其中一個屬性的 <xref:System.Printing.ValidationResult>。</span><span class="sxs-lookup"><span data-stu-id="e822d-125">This returns a <xref:System.Printing.ValidationResult> that includes the new <xref:System.Printing.PrintTicket> as one of its properties.</span></span>  
  
5. <span data-ttu-id="e822d-126">然後，此範例會測試新的 <xref:System.Printing.PrintTicket> 是否要求雙工。</span><span class="sxs-lookup"><span data-stu-id="e822d-126">The sample then tests that the new <xref:System.Printing.PrintTicket> requests duplexing.</span></span> <span data-ttu-id="e822d-127">如果有，則範例會使其成為使用者的新預設列印票證。</span><span class="sxs-lookup"><span data-stu-id="e822d-127">If it does, then the sample makes it the new default print ticket for the user.</span></span> <span data-ttu-id="e822d-128">如果上述步驟2已被省略，而且印表機不支援長時間的雙面處理，則測試會導致 `false`。</span><span class="sxs-lookup"><span data-stu-id="e822d-128">If step 2 above had been left out and the printer did not support duplexing along the long side, then the test would have resulted in `false`.</span></span> <span data-ttu-id="e822d-129">（請參閱上面的注意事項）。</span><span class="sxs-lookup"><span data-stu-id="e822d-129">(See the note above.)</span></span>  
  
6. <span data-ttu-id="e822d-130">最後一個重要步驟是使用 <xref:System.Printing.PrintQueue.Commit%2A> 方法，將變更認可至 <xref:System.Printing.PrintQueue> 的 <xref:System.Printing.PrintQueue.UserPrintTicket%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e822d-130">The last significant step is to commit the change to the <xref:System.Printing.PrintQueue.UserPrintTicket%2A> property of the <xref:System.Printing.PrintQueue> with the <xref:System.Printing.PrintQueue.Commit%2A> method.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 <span data-ttu-id="e822d-131">如此一來，您就可以快速測試此範例，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e822d-131">So that you can quickly test this example, the remainder of it is presented below.</span></span> <span data-ttu-id="e822d-132">建立專案和命名空間，然後將本文中的兩個程式碼片段貼入命名空間區塊。</span><span class="sxs-lookup"><span data-stu-id="e822d-132">Create a project and a namespace and then paste both the code snippets in this article into the namespace block.</span></span>  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a><span data-ttu-id="e822d-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="e822d-133">See also</span></span>

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [<span data-ttu-id="e822d-134">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="e822d-134">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="e822d-135">列印概觀</span><span class="sxs-lookup"><span data-stu-id="e822d-135">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="e822d-136">列印架構</span><span class="sxs-lookup"><span data-stu-id="e822d-136">Print Schema</span></span>](https://go.microsoft.com/fwlink/?LinkId=186397)
