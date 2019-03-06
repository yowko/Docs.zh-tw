---
title: HOW TO：啟用文字修剪
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 367e1f46524d8135d8269a2e2159dfe7c2468c45
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354462"
---
# <a name="how-to-enable-text-trimming"></a>HOW TO：啟用文字修剪
此範例示範使用方式和效果中的可用值<xref:System.Windows.TextTrimming>列舉型別。  
  
## <a name="example"></a>範例  
 下列範例會定義<xref:System.Windows.Controls.TextBlock>具有項目<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>屬性設定。  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a>範例  
 設定對應<xref:System.Windows.TextTrimming>在程式碼中的屬性以下所示。  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 目前三個選項可修剪文字：**CharacterEllipsis**， **WordEllipsis**，以及**None**。  
  
 當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設定為**CharacterEllipsis**，會修剪文字，並繼續使用省略符號在最接近修剪邊緣的字元。  此設定是要修剪文字，使其更接近修剪界限，但可能會導致部分修剪文字。  下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>類似上面所定義。  
  
 ![例如：TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")  
  
 當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設定為**WordEllipsis**，會修剪文字，並繼續使用最接近修剪邊緣的第一個完整文字結尾的省略符號。  此設定不會顯示部分修剪的文字，但傾向不修剪的文字修剪邊緣**CharacterEllipsis**設定。  下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>上面所定義。  
  
 ![例如：TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")  
  
 當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設定為**無**，會執行任何的文字修剪。  在此情況下，只會將文字裁剪到父文字容器的界限。  下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>類似上面所定義。  
  
 ![例如：TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")
