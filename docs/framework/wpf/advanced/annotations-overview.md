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
ms.openlocfilehash: dc9c4125f9ac3c44be41efe92b9e495599e5c130
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004042"
---
# <a name="annotations-overview"></a>附註概觀
在書面文件上撰寫附註或註解是相當稀鬆平常的事，我們幾乎將它視為理所當然。 這些附註或註解是我們新增至文件的「註釋」，用以標記資訊，或反白顯示感興趣的項目以供日後參考。 雖然在書面文件上撰寫附註很容易且平常，不過在電子文件中新增個人註解的功能通常非常有限，如果有的話。  
  
 本主題會回顧數個常見的批註類型，特別是附注和醒目提示，並說明 Microsoft 注釋架構如何透過 Windows Presentation Foundation 在應用程式中協助這些類型的注釋（WPF）檔視圖控制項。  支援注釋的 @no__t 0 檔視圖控制項包括 <xref:System.Windows.Controls.FlowDocumentReader> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer>，以及從 <xref:System.Windows.Controls.Primitives.DocumentViewerBase> （例如 <xref:System.Windows.Controls.DocumentViewer> 和 <xref:System.Windows.Controls.FlowDocumentPageViewer>）衍生的控制項。  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>自黏便箋  
 典型的自黏便箋包含寫在一小張色紙上，然後「黏」在文件上的資訊。 數位便箋為電子檔提供類似的功能，但有額外的彈性可包含許多其他類型的內容，例如輸入文字、手寫附注（例如 Tablet PC 「筆跡」筆劃）或 Web 連結。  
  
 下圖顯示一些反白顯示、文字自黏便箋和筆跡自黏便箋註釋的範例。  
  
 ![反白顯示、文字和筆跡自黏便箋註釋。](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 下列範例顯示您可用來在應用程式中啟用註釋支援的方法。  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>反白顯示  
 人們使用有創意的方法，在標記書面文件時將注意力吸引到感興趣的項目，例如使用底線、反白顯示、圈起句子中的文字，或是在邊界繪製記號或標記法。  Microsoft 注釋架構中的反白顯示批註提供了類似的功能，用來標記 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 檔視圖控制項中顯示的資訊。  
  
 下圖顯示反白顯示註釋的範例。  
  
 ![反白顯示註釋](./media/caf-callouts.png "CAF_Callouts")  
  
 使用者通常會藉由先選取一些文字或感關注的專案來建立批註，然後以滑鼠右鍵按一下以顯示 <xref:System.Windows.Controls.ContextMenu> 的注釋選項。  下列範例顯示 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，您可以用來宣告具有路由命令的 <xref:System.Windows.Controls.ContextMenu>，讓使用者可以存取來建立和管理注釋。  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>資料錨定  
 注釋架構會將注釋系結至使用者所選取的資料，而不只是顯示在顯示視圖上的位置。 因此，如果文件檢視變更，例如當使用者捲動或調整顯示視窗大小時，註釋會與它繫結的資料選取範圍在一起。 例如，下圖說明使用者對文字選取範圍所做的註釋。 當文件檢視變更時 (捲動、調整大小、縮放比例或其他移動)，反白顯示註釋會隨著原始資料選取範圍移動。  
  
 ![註釋資料錨定](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>比對註釋與標註物件  
 您可以比對註釋與對應的標註物件。 例如，請考慮具有註解窗格的簡單文件讀取應用程式。 註解窗格可能是清單方塊，其中顯示來自錨定到文件之註釋清單的文字。 如果使用者在清單方塊中選取項目，則應用程式會將對應註釋物件所錨定之文件中的段落帶入檢視。  
  
 下列範例示範如何為這類作為註解窗格的清單方塊實作事件處理常式。  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 另一個範例案例牽涉到可透過電子郵件在檔讀取器之間交換注釋和便箋的應用程式。 這項功能讓這些應用程式可讓讀者巡覽至包含要交換之註釋的頁面。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [附註結構描述](annotations-schema.md)
- [ContextMenu 概觀](../controls/contextmenu-overview.md)
- [命令概觀](commanding-overview.md)
- [非固定格式文件概觀](flow-document-overview.md)
- [如何：將命令新增至 MenuItem @ no__t-0
