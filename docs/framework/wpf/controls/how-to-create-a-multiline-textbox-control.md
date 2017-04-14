---
title: "如何：建立多行 TextBox 控制項 | Microsoft Docs"
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
  - "TextBox 控制項, 多行文字"
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：建立多行 TextBox 控制項
本範例示範如何使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定義 <xref:System.Windows.Controls.TextBox> 控制項，該控制項會自動擴充以容納多行文字。  
  
## 範例  
 如果將 <xref:System.Windows.Controls.TextBox.TextWrapping%2A> 屬性設為 **Wrap**，會使得輸入的文字在碰到 <xref:System.Windows.Controls.TextBox> 控制項的邊緣時換行，必要時會自動擴充 <xref:System.Windows.Controls.TextBox> 控制項，以包含給新行的空間。  
  
 如果將 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> 屬性設為 **true**，會在按下 RETURN 鍵時插入新行，同樣地，必要時會自動擴充 <xref:System.Windows.Controls.TextBox>，以包含給新行的空間。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> 屬性會將捲軸加入至 <xref:System.Windows.Controls.TextBox>，以在 <xref:System.Windows.Controls.TextBox> 的內容 <xref:System.Windows.Controls.TextBox> 擴充超過外圍框架或視窗的大小時，可以加以捲動。  
  
 [!code-xml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## 請參閱  
 <xref:System.Windows.TextWrapping>   
 [TextBox 概觀](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox 概觀](../../../../docs/framework/wpf/controls/richtextbox-overview.md)