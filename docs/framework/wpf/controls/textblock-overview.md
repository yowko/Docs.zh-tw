---
title: "TextBlock 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TextBlock 控制項"
  - "TextBlock 控制項"
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# TextBlock 概觀
<xref:System.Windows.Controls.TextBlock>控制項提供有彈性的文字支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 項目主要針對 basic[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]案例不需要多個段落的文字。 它支援許多屬性，啟用精確控制項的呈現方式，例如<xref:System.Windows.Controls.TextBlock.FontFamily%2A>， <xref:System.Windows.Controls.TextBlock.FontSize%2A>， <xref:System.Windows.Controls.TextBlock.FontWeight%2A>， <xref:System.Windows.Controls.TextBlock.TextEffects%2A>，和<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>。 文字內容可以使用加入<xref:System.Windows.Controls.TextBlock.Text%2A>屬性。 當用於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，開啟和結尾標記之間的內容會隱含地新增做為項目的文字。  
  
 A <xref:System.Windows.Controls.TextBlock>項目可以具現化很簡單地使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 同樣地，使用<xref:System.Windows.Controls.TextBlock>程式碼中的項目是相當簡單。  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Label>