---
title: "使用圖像繪製文字 | Microsoft Docs"
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
  - "使用 Glyphs 物件繪製的文字"
  - "繪製文字的圖像 （glyph） 物件"
  - "印刷樣式圖像 （glyph） 的物件"
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 使用圖像繪製文字
本主題說明如何使用低階<xref:System.Windows.Documents.Glyphs>物件，以顯示在文字[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
## <a name="example"></a>範例  
 下列範例顯示如何定義屬性<xref:System.Windows.Documents.Glyphs>物件存放至[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 <xref:System.Windows.Documents.Glyphs>物件所表示的輸出<xref:System.Windows.Media.GlyphRun>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 這些範例假設新細明體，新細明體和新細明體字型會安裝在本機電腦上的 C:\WINDOWS\Fonts 資料夾。  
  
 [!code-xml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 這個範例示範如何定義的其他屬性<xref:System.Windows.Documents.Glyphs>物件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>另請參閱  
 [在 WPF 中的印刷樣式](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)