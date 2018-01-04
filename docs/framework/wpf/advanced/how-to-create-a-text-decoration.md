---
title: "如何：建立文字裝飾"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0beb22ba78c6fc99951bc2d780c1c5defa32e637
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-text-decoration"></a>如何：建立文字裝飾
A<xref:System.Windows.TextDecoration>物件是視覺裝飾，您可以加入文字。 文字裝飾的四種類型： 底線、 基準、 刪除線和頂線。 下列範例顯示相對於文字的文字裝飾的位置。  
  
 ![文字裝飾位置的圖表](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")  
文字裝飾類型的範例  
  
 若要加入文字的文字裝飾，請建立<xref:System.Windows.TextDecoration>物件，並修改其屬性。 使用<xref:System.Windows.TextDecoration.Location%2A>屬性來指定文字裝飾的出現位置，例如底線。 使用<xref:System.Windows.TextDecoration.Pen%2A>屬性來指定文字裝飾，例如純色填滿或漸層色彩的外觀。 如果您未指定的值<xref:System.Windows.TextDecoration.Pen%2A>屬性，為相同的色彩做為文字的裝飾預設值。 一旦定義了<xref:System.Windows.TextDecoration>物件、 將它加入<xref:System.Windows.TextDecorations>想要的文字之物件的集合。  
  
 下列範例示範設定線性漸層筆刷與虛線的畫筆樣式的文字裝飾。  
  
 ![線性漸層底線的文字裝飾](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")  
範例中的底線樣式以線性漸層筆刷和虛線的畫筆  
  
 <xref:System.Windows.Documents.Hyperlink>物件是可讓您將主機動態內容內的超連結的內嵌層級流動內容項目。 根據預設，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件，以顯示底線。 <xref:System.Windows.TextDecoration>物件可以是具現化，耗用的效能，特別是如果您有許多<xref:System.Windows.Documents.Hyperlink>物件。 若要大量使用<xref:System.Windows.Documents.Hyperlink>項目，您可能要考慮這類觸發事件時，才顯示底線<xref:System.Windows.ContentElement.MouseEnter>事件。  
  
 在下列範例中，"My MSN 」 連結的底線是動態的它只會<xref:System.Windows.ContentElement.MouseEnter>觸發事件。  
  
 ![顯示 Textdecoration 的超連結](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
定義與 Textdecoration 的超連結  
  
 如需詳細資訊，請參閱[指定超連結是否要加上底線](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)。  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，底線文字裝飾會使用預設字型值。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 在下列程式碼範例中，使用畫筆的單色筆刷建立底線文字裝飾。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 在下列程式碼範例中，底線文字裝飾會建立與虛線畫筆線性漸層筆刷。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [指定超連結是否要加上底線](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
