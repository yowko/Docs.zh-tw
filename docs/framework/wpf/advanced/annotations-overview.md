---
title: "附註概觀 | Microsoft Docs"
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
  - "文件, 附註"
  - "反白顯示"
  - "自黏便箋"
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 附註概觀
在書面文件上撰寫備註或註解是相當普遍的活動，導致一般人幾乎都將它視為理所當然。  這些備註或註解是我們加入文件的「附註」，以標記資訊或特別標明有興趣的項目，以供日後參照。  雖然在書面文件上撰寫備註很容易，但是在電子文件上加入個人註解的功能通常非常有限或根本完全無法使用。  
  
 本主題將回顧幾種常見的附註類型 \(特別是自黏便箋和醒目提示\)，並說明 [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] 如何透過 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 文件檢視控制項，在應用程式中使用這幾種附註類型。  支援附註的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 文件檢視控制項包括 <xref:System.Windows.Controls.FlowDocumentReader> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer>，以及衍生自 <xref:System.Windows.Controls.Primitives.DocumentViewerBase> 的控制項，例如 <xref:System.Windows.Controls.DocumentViewer> 和 <xref:System.Windows.Controls.FlowDocumentPageViewer>。  
  
   
  
<a name="caf1_type_stickynotes"></a>   
## 自黏便箋  
 一般自黏便箋是將資訊寫在彩色便條紙，然後再將便條紙「貼」在文件上。  數位自黏便箋為電子文件提供類似的功能，但是增加了彈性，使您可以加入其他許多不同類型的內容，諸如輸入文字、手寫備註 \(如 [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]「筆墨」筆劃\) 或 Web 連結等。  
  
 下圖顯示醒目提示、文字自黏便箋和筆墨自黏便箋等附註的部分範例。  
  
 ![反白顯示、文字和筆跡自黏便箋註釋。](../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF\_StickyNote")  
  
 下列範例示範可以在應用程式中啟用附註支援的方法。  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## 醒目提示  
 一般人在標記書面文件時，都會使用有創意的方法將注意力集中在有興趣的項目上，例如使用底線、螢光筆、或畫圈的方式標出重要的字句，或是在空白處畫記號或加上備註。  [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] 中的醒目提示附註提供了類似的功能，可以用來標記顯示在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 文件檢視控制項中的資訊。  
  
 下圖顯示醒目提示附註的範例。  
  
 ![反白顯示註釋](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF\_Callouts")  
  
 使用者建立附註的方式通常是先選取某段文字或有興趣的項目，然後再按一下滑鼠右鍵，顯示附註選項的 <xref:System.Windows.Controls.ContextMenu>。  下列範例顯示 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，可用來宣告 <xref:System.Windows.Controls.ContextMenu>，供使用者存取可以用來建立及管理附註的路由命令。  
  
 [!code-xml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## 資料錨定  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] 可將附註繫結到使用者選取的資料，而不是只繫結到畫面顯示的位置。  因此，如果文件檢視發生變更，例如當使用者捲動顯示視窗或調整其大小時，附註仍會跟隨著它所繫結的資料選取範圍。  例如，下圖顯示使用者在文字選取範圍所做的附註。  當文件檢視變更 \(捲動、調整大小、縮放或其他移動方式\) 時，醒目提示附註會隨著原始資料選取範圍一起移動。  
  
 ![註釋資料錨定](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF\_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## 附註和標註物件配對  
 您可以針對附註與對應的標註物件進行配對。  例如，假設某個簡單的文件讀取應用程式具有註解窗格，  註解窗格可能是清單方塊，會在錨定至文件的附註清單中顯示文字。  如果使用者選取清單方塊中的項目，應用程式就會在檢視中顯示對應附註物件錨定的文件段落。  
  
 下列範例示範如何實作當做註解窗格之清單方塊的事件處理常式 \(Event Handler\)。  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 另一個範例案例牽涉到可以透過電子郵件在文件讀取器 \(Reader\) 之間交換附註和自黏便箋的應用程式。  這項功能使這些應用程式可以在讀取器中巡覽到內含要交換之附註的頁面。  
  
## 請參閱  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>   
 <xref:System.Windows.Controls.DocumentViewer>   
 <xref:System.Windows.Controls.FlowDocumentPageViewer>   
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>   
 <xref:System.Windows.Controls.FlowDocumentReader>   
 <xref:System.Windows.Annotations.IAnchorInfo>   
 [附註結構描述](../../../../docs/framework/wpf/advanced/annotations-schema.md)   
 [ContextMenu 概觀](../../../../docs/framework/wpf/controls/contextmenu-overview.md)   
 [命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [非固定格式文件概觀](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [How to: Add a Command to a MenuItem](http://msdn.microsoft.com/zh-tw/013d68a0-5373-4a68-bd91-5de574307370)