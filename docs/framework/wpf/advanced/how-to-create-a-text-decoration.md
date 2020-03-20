---
title: 如何：建立文字裝飾
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
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185928"
---
# <a name="how-to-create-a-text-decoration"></a>如何：建立文字裝飾
物件<xref:System.Windows.TextDecoration>是可以添加到文本的視覺修飾。 有四種類型的文本修飾：底線、基線、擊穿和過線。 下面的示例顯示文本修飾相對於文本的位置。  
  
 ![文本修飾類型圖](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 要向文本添加文本修飾，請創建物件<xref:System.Windows.TextDecoration>並修改其屬性。 使用<xref:System.Windows.TextDecoration.Location%2A>屬性指定文本修飾的顯示位置，如底線。 使用<xref:System.Windows.TextDecoration.Pen%2A>屬性指定文本修飾的外觀，如實心填充或漸變顏色。 如果不為<xref:System.Windows.TextDecoration.Pen%2A>屬性指定值，則修飾預設為與文本相同的顏色。 定義物件<xref:System.Windows.TextDecoration>後，將其添加到所需文本物件<xref:System.Windows.TextDecorations>的集合中。  
  
 下面的示例顯示了使用線性漸層畫筆和虛線筆進行樣式設置的文本修飾。  
  
 ![具有線性漸層底線的文字裝飾](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 該<xref:System.Windows.Documents.Hyperlink>物件是一個內聯級流內容元素，允許您在流內容中託管超連結。 預設情況下，<xref:System.Windows.Documents.Hyperlink>使用<xref:System.Windows.TextDecoration>物件顯示底線。 <xref:System.Windows.TextDecoration>物件可以執行密集型具現化，尤其是在有許多<xref:System.Windows.Documents.Hyperlink>物件時。 如果廣泛使用<xref:System.Windows.Documents.Hyperlink>元素，則可能需要考慮僅在觸發事件（如<xref:System.Windows.ContentElement.MouseEnter>事件）時顯示底線。  
  
 在下面的示例中，"我的 MSN"連結的底線是動態的 ，它僅在觸發<xref:System.Windows.ContentElement.MouseEnter>事件時才出現。  
  
 ![顯示 TextDecoration 的超連結](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 如需詳細資訊，請參閱[指定超連結是否要加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)。  
  
## <a name="example"></a>範例  
 在下面的代碼示例中，底線文本修飾使用預設字型值。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 在下面的代碼示例中，使用筆的單色筆刷創建底線文本修飾。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 在下面的代碼示例中，使用虛線筆的線性漸層畫筆創建底線文本修飾。  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [指定超連結是否加上底線](how-to-specify-whether-a-hyperlink-is-underlined.md)
