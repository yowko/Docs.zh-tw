---
title: "如何：啟用文字修剪 | Microsoft Docs"
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
  - "文件, 修剪文字"
  - "文字, 修剪"
  - "修剪文字"
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：啟用文字修剪
這個範例示範 <xref:System.Windows.TextTrimming> 列舉型別中可用值的使用方式和效果。  
  
## 範例  
 下列範例定義已設定 <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> 屬性的 <xref:System.Windows.Controls.TextBlock> 項目。  
  
 [!code-xml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## 範例  
 下面示範如何以程式碼設定對應的 <xref:System.Windows.TextTrimming> 屬性。  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 目前有三種修剪文字選項：**CharacterEllipsis**、**WordEllipsis** 和 **None**。  
  
 當 <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> 設定為 **CharacterEllipsis** 時，會修剪文字，而且會在最接近修剪邊緣的字元處加上省略符號。  這項設定是要修剪文字，使其較接近修剪界限，但是可能會導致字組遭到局部修剪。  下圖顯示這項設定在 <xref:System.Windows.Controls.TextBlock> 上的效果 \(與上面定義的項目類似\)。  
  
 ![範例：TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming\_Character")  
  
 當 <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> 設定為 **WordEllipsis** 時，會修剪文字，而且會在最接近修剪邊緣的第一個完整字組結尾處加上省略符號。  這項設定不會顯示局部修剪的字組，但是也不會修剪文字，使其接近 **CharacterEllipsis** 設定的修剪邊緣。  下圖顯示這項設定對上面定義之 <xref:System.Windows.Controls.TextBlock> 的效果。  
  
 ![範例：TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming\_Word")  
  
 當 <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> 設定為 **None** 時，不會執行任何文字修剪。  在這種情況下，只會將文字裁剪至父文字容器的界限。  下圖顯示這項設定在 <xref:System.Windows.Controls.TextBlock> 上的效果 \(與上面定義的項目類似\)。  
  
 ![範例：TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming\_None")