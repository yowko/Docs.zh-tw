---
title: "如何：將 Stretch 屬性套用至 Viewbox 的內容 | Microsoft Docs"
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
  - "控制項, Viewbox"
  - "Stretch 屬性"
  - "StretchDirection 屬性"
  - "Viewbox 控制項"
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：將 Stretch 屬性套用至 Viewbox 的內容
## 範例  
 本範例說明如何變更 <xref:System.Windows.Controls.Viewbox> 的 <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> 和 <xref:System.Windows.Controls.Viewbox.Stretch%2A> 屬性值。  
  
 第一個範例會使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定義 <xref:System.Windows.Controls.Viewbox> 項目。  它會指派值為 400 的 <xref:System.Windows.FrameworkElement.MaxWidth%2A> 和 <xref:System.Windows.FrameworkElement.MaxHeight%2A>。  此範例會在 <xref:System.Windows.Controls.Viewbox> 內將 <xref:System.Windows.Controls.Image> 項目巢狀化。  對應於 <xref:System.Windows.Controls.Viewbox.Stretch%2A> 與 <xref:System.Windows.Controls.StretchDirection> 列舉之屬性值的 <xref:System.Windows.Controls.Button> 項目，會管理巢狀 <xref:System.Windows.Controls.Image> 的自動縮放行為。  
  
 [!code-xml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 下列程式碼後置檔案會處理 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件，這些事件是由之前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 範例所定義。  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## 請參閱  
 <xref:System.Windows.Controls.Viewbox>   
 <xref:System.Windows.Media.Stretch>   
 <xref:System.Windows.Controls.StretchDirection>