---
title: 附註概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
ms.openlocfilehash: 433fee08d44720640d3f9d1bf2511a6a267eb58e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145458"
---
# <a name="annotations-overview"></a><span data-ttu-id="6b6df-102">附註概觀</span><span class="sxs-lookup"><span data-stu-id="6b6df-102">Annotations Overview</span></span>
<span data-ttu-id="6b6df-103">在書面文件上撰寫附註或註解是相當稀鬆平常的事，我們幾乎將它視為理所當然。</span><span class="sxs-lookup"><span data-stu-id="6b6df-103">Writing notes or comments on paper documents is such a commonplace activity that we almost take it for granted.</span></span> <span data-ttu-id="6b6df-104">這些附註或註解是我們新增至文件的「註釋」，用以標記資訊，或反白顯示感興趣的項目以供日後參考。</span><span class="sxs-lookup"><span data-stu-id="6b6df-104">These notes or comments are "annotations" that we add to a document to flag information or to highlight items of interest for later reference.</span></span> <span data-ttu-id="6b6df-105">雖然在書面文件上撰寫附註很容易且平常，不過在電子文件中新增個人註解的功能通常非常有限，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="6b6df-105">Although writing notes on printed documents is easy and commonplace, the ability to add personal comments to electronic documents is typically very limited, if available at all.</span></span>  
  
 <span data-ttu-id="6b6df-106">本主題回顧了幾種常見類型的注釋，特別是便箋和亮點，並說明了 Microsoft 注釋框架如何通過 Windows 演示基礎 （WPF） 在應用程式中促進這些類型的注釋） 文檔查看控制項。</span><span class="sxs-lookup"><span data-stu-id="6b6df-106">This topic reviews several common types of annotations, specifically sticky notes and highlights, and illustrates how the Microsoft Annotations Framework facilitates these types of annotations in applications through the Windows Presentation Foundation (WPF) document viewing controls.</span></span>  <span data-ttu-id="6b6df-107">WPF 文檔查看控制項<xref:System.Windows.Controls.FlowDocumentReader>支援注釋包括 和<xref:System.Windows.Controls.FlowDocumentScrollViewer>，以及派生自<xref:System.Windows.Controls.Primitives.DocumentViewerBase>等<xref:System.Windows.Controls.DocumentViewer><xref:System.Windows.Controls.FlowDocumentPageViewer>的控制項。</span><span class="sxs-lookup"><span data-stu-id="6b6df-107">WPF document viewing controls that support annotations include <xref:System.Windows.Controls.FlowDocumentReader> and <xref:System.Windows.Controls.FlowDocumentScrollViewer>, as well as controls derived from <xref:System.Windows.Controls.Primitives.DocumentViewerBase> such as <xref:System.Windows.Controls.DocumentViewer> and <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span></span>  

<a name="caf1_type_stickynotes"></a>
## <a name="sticky-notes"></a><span data-ttu-id="6b6df-108">自黏便箋</span><span class="sxs-lookup"><span data-stu-id="6b6df-108">Sticky Notes</span></span>  
 <span data-ttu-id="6b6df-109">典型的自黏便箋包含寫在一小張色紙上，然後「黏」在文件上的資訊。</span><span class="sxs-lookup"><span data-stu-id="6b6df-109">A typical sticky note contains information written on a small piece of colored paper that is then "stuck" to a document.</span></span> <span data-ttu-id="6b6df-110">數位便箋為電子文檔提供了類似的功能，但增加了包含許多其他類型的內容的靈活性，如鍵入的文字、手寫筆記（例如 Tablet PC"墨蹟"筆劃）或 Web 連結。</span><span class="sxs-lookup"><span data-stu-id="6b6df-110">Digital sticky notes provide similar functionality for electronic documents, but with the added flexibility to include many other types of content such as typed text, handwritten notes (for example, Tablet PC "ink" strokes), or Web links.</span></span>  
  
 <span data-ttu-id="6b6df-111">下圖顯示一些反白顯示、文字自黏便箋和筆跡自黏便箋註釋的範例。</span><span class="sxs-lookup"><span data-stu-id="6b6df-111">The following illustration shows some examples of highlight, text sticky note, and ink sticky note annotations.</span></span>  
  
 <span data-ttu-id="6b6df-112">![反白顯示、文字和筆跡自黏便箋註釋。](./media/caf-stickynote.jpg "CAF_StickyNote")</span><span class="sxs-lookup"><span data-stu-id="6b6df-112">![Highlight, text and ink sticky note annotations.](./media/caf-stickynote.jpg "CAF_StickyNote")</span></span>  
  
 <span data-ttu-id="6b6df-113">下列範例顯示您可用來在應用程式中啟用註釋支援的方法。</span><span class="sxs-lookup"><span data-stu-id="6b6df-113">The following example shows the method that you can use to enable annotation support in your application.</span></span>  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>
## <a name="highlights"></a><span data-ttu-id="6b6df-114">重點摘要</span><span class="sxs-lookup"><span data-stu-id="6b6df-114">Highlights</span></span>  
 <span data-ttu-id="6b6df-115">人們使用有創意的方法，在標記書面文件時將注意力吸引到感興趣的項目，例如使用底線、反白顯示、圈起句子中的文字，或是在邊界繪製記號或標記法。</span><span class="sxs-lookup"><span data-stu-id="6b6df-115">People use creative methods to draw attention to items of interest when they mark up a paper document, such as underlining, highlighting, circling words in a sentence, or drawing marks or notations in the margin.</span></span>  <span data-ttu-id="6b6df-116">Microsoft 注釋框架中的突出顯示注釋提供了用於標記 WPF 文檔查看控制項中顯示的資訊的類似功能。</span><span class="sxs-lookup"><span data-stu-id="6b6df-116">Highlight annotations in Microsoft Annotations Framework provide a similar feature for marking up information displayed in WPF document viewing controls.</span></span>  
  
 <span data-ttu-id="6b6df-117">下圖顯示反白顯示註釋的範例。</span><span class="sxs-lookup"><span data-stu-id="6b6df-117">The following illustration shows an example of a highlight annotation.</span></span>  
  
 <span data-ttu-id="6b6df-118">![反白顯示註釋](./media/caf-callouts.png "CAF_Callouts")</span><span class="sxs-lookup"><span data-stu-id="6b6df-118">![Highlight Annotation](./media/caf-callouts.png "CAF_Callouts")</span></span>  
  
 <span data-ttu-id="6b6df-119">使用者通常先選擇某些文本或感興趣的項，然後按右鍵以顯示注釋<xref:System.Windows.Controls.ContextMenu>選項來創建批註。</span><span class="sxs-lookup"><span data-stu-id="6b6df-119">Users typically create annotations by first selecting some text or an item of interest, and then right-clicking to display a <xref:System.Windows.Controls.ContextMenu> of annotation options.</span></span>  <span data-ttu-id="6b6df-120">下面的示例顯示了[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]可用於聲明<xref:System.Windows.Controls.ContextMenu>具有路由命令的，使用者可以訪問這些命令以創建和管理批註。</span><span class="sxs-lookup"><span data-stu-id="6b6df-120">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] you can use to declare a <xref:System.Windows.Controls.ContextMenu> with routed commands that users can access to create and manage annotations.</span></span>  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>
## <a name="data-anchoring"></a><span data-ttu-id="6b6df-121">資料錨定</span><span class="sxs-lookup"><span data-stu-id="6b6df-121">Data Anchoring</span></span>  
 <span data-ttu-id="6b6df-122">注釋框架將注釋綁定到使用者選擇的資料，而不僅僅是將注釋綁定到顯示視圖中的位置。</span><span class="sxs-lookup"><span data-stu-id="6b6df-122">The Annotations Framework binds annotations to the data that the user selects, not just to a position on the display view.</span></span> <span data-ttu-id="6b6df-123">因此，如果文件檢視變更，例如當使用者捲動或調整顯示視窗大小時，註釋會與它繫結的資料選取範圍在一起。</span><span class="sxs-lookup"><span data-stu-id="6b6df-123">Therefore, if the document view changes, such as when the user scrolls or resizes the display window, the annotation stays with the data selection to which it is bound.</span></span> <span data-ttu-id="6b6df-124">例如，下圖說明使用者對文字選取範圍所做的註釋。</span><span class="sxs-lookup"><span data-stu-id="6b6df-124">For example, the following graphic illustrates an annotation that the user has made on a text selection.</span></span> <span data-ttu-id="6b6df-125">當文件檢視變更時 (捲動、調整大小、縮放比例或其他移動)，反白顯示註釋會隨著原始資料選取範圍移動。</span><span class="sxs-lookup"><span data-stu-id="6b6df-125">When the document view changes (scrolls, resizes, scales, or otherwise moves), the highlight annotation moves with the original data selection.</span></span>  
  
 <span data-ttu-id="6b6df-126">![註釋資料錨定](./media/caf-dataanchoring.png "CAF_DataAnchoring")</span><span class="sxs-lookup"><span data-stu-id="6b6df-126">![Annotation Data Anchoring](./media/caf-dataanchoring.png "CAF_DataAnchoring")</span></span>  
  
<a name="matching_annotations_with_annotated_objects"></a>
## <a name="matching-annotations-with-annotated-objects"></a><span data-ttu-id="6b6df-127">比對註釋與標註物件</span><span class="sxs-lookup"><span data-stu-id="6b6df-127">Matching Annotations with Annotated Objects</span></span>  
 <span data-ttu-id="6b6df-128">您可以比對註釋與對應的標註物件。</span><span class="sxs-lookup"><span data-stu-id="6b6df-128">You can match annotations with the corresponding annotated objects.</span></span> <span data-ttu-id="6b6df-129">例如，請考慮具有註解窗格的簡單文件讀取應用程式。</span><span class="sxs-lookup"><span data-stu-id="6b6df-129">For example, consider a simple document reader application that has a comments pane.</span></span> <span data-ttu-id="6b6df-130">註解窗格可能是清單方塊，其中顯示來自錨定到文件之註釋清單的文字。</span><span class="sxs-lookup"><span data-stu-id="6b6df-130">The comments pane might be a list box that displays the text from a list of annotations that are anchored to a document.</span></span> <span data-ttu-id="6b6df-131">如果使用者在清單方塊中選取項目，則應用程式會將對應註釋物件所錨定之文件中的段落帶入檢視。</span><span class="sxs-lookup"><span data-stu-id="6b6df-131">If the user selects an item in the list box, then the application brings into view the paragraph in the document that the corresponding annotation object is anchored to.</span></span>  
  
 <span data-ttu-id="6b6df-132">下列範例示範如何為這類作為註解窗格的清單方塊實作事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6b6df-132">The following example demonstrates how to implement the event handler of such a list box that serves as the comments pane.</span></span>  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 <span data-ttu-id="6b6df-133">另一個示例方案涉及應用程式，這些應用程式允許通過電子郵件在文檔閱讀器之間交換注釋和便箋。</span><span class="sxs-lookup"><span data-stu-id="6b6df-133">Another example scenario involves applications that enable the exchange of annotations and sticky notes between document readers through email.</span></span> <span data-ttu-id="6b6df-134">這項功能讓這些應用程式可讓讀者巡覽至包含要交換之註釋的頁面。</span><span class="sxs-lookup"><span data-stu-id="6b6df-134">This feature enables these applications to navigate the reader to the page that contains the annotation that is being exchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b6df-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b6df-135">See also</span></span>

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [<span data-ttu-id="6b6df-136">註釋結構描述</span><span class="sxs-lookup"><span data-stu-id="6b6df-136">Annotations Schema</span></span>](annotations-schema.md)
- [<span data-ttu-id="6b6df-137">ContextMenu 概觀</span><span class="sxs-lookup"><span data-stu-id="6b6df-137">ContextMenu Overview</span></span>](../controls/contextmenu-overview.md)
- [<span data-ttu-id="6b6df-138">命令概觀</span><span class="sxs-lookup"><span data-stu-id="6b6df-138">Commanding Overview</span></span>](commanding-overview.md)
- [<span data-ttu-id="6b6df-139">非固定格式文件概觀</span><span class="sxs-lookup"><span data-stu-id="6b6df-139">Flow Document Overview</span></span>](flow-document-overview.md)
- <span data-ttu-id="6b6df-140">[如何：將命令新增至 MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6b6df-140">[How to: Add a Command to a MenuItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))</span></span>
