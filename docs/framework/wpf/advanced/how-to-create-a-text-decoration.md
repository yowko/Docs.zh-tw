---
title: HOW TO：建立文字裝飾
ms.date: 03/30/2017
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
ms.openlocfilehash: d586eef8d1308070da38a0a54c63c3ba64d30c8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133831"
---
# <a name="how-to-create-a-text-decoration"></a>HOW TO：建立文字裝飾
A<xref:System.Windows.TextDecoration>物件是您可以新增至文字的視覺裝飾。 有四種類型的文字裝飾： 底線、 基準、 刪除線和頂線。 下列範例顯示的文字裝飾，相對於文字的位置。  
  
 ![文字裝飾類型的圖表](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 若要加入文字裝飾的文字，建立<xref:System.Windows.TextDecoration>物件，並修改其屬性。 使用<xref:System.Windows.TextDecoration.Location%2A>屬性來指定文字裝飾的出現位置，例如底線。 使用<xref:System.Windows.TextDecoration.Pen%2A>屬性來指定文字裝飾，例如純色填滿或漸層色彩的外觀。 如果您未指定的值<xref:System.Windows.TextDecoration.Pen%2A>屬性，則裝飾會預設為相同的文字色彩。 一旦您已定義<xref:System.Windows.TextDecoration>物件，將它新增至<xref:System.Windows.TextDecorations>想要的文字物件的集合。  
  
 下列範例顯示線性漸層筆刷與虛線的畫筆設定樣式的文字裝飾。  
  
 ![具有線性漸層底線的文字裝飾](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <xref:System.Windows.Documents.Hyperlink>物件是內嵌層級非固定格式內容項目，可讓您將非固定格式內容內超連結。 根據預設，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件，以顯示底線。 <xref:System.Windows.TextDecoration> 物件可以具現化，需要大量的效能，特別是如果您有許多<xref:System.Windows.Documents.Hyperlink>物件。 若要大量使用<xref:System.Windows.Documents.Hyperlink>項目，您可能要考慮這類觸發事件時，才顯示底線<xref:System.Windows.ContentElement.MouseEnter>事件。  
  
 在下列範例中，「 我的 MSN 」 連結，底線是動態的它才會出現<xref:System.Windows.ContentElement.MouseEnter>觸發事件。  
  
 ![顯示 TextDecoration 的超連結](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  
   
 如需詳細資訊，請參閱[指定超連結是否要加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)。  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，底線文字裝飾會使用預設字型值。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 在下列程式碼範例中，底線文字裝飾會使用畫筆的單色筆刷。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 在下列程式碼範例中，底線文字裝飾會以虛線的畫筆線性漸層筆刷。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [指定超連結是否要加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)
