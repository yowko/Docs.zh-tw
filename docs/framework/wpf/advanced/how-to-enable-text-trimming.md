---
title: "如何：啟用文字修剪"
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
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdaafa62815c75d8ab364a18d909d867f90052c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-text-trimming"></a>如何：啟用文字修剪
此範例示範的使用方式和中的可用值的效果<xref:System.Windows.TextTrimming>列舉型別。  
  
## <a name="example"></a>範例  
 下列範例會定義<xref:System.Windows.Controls.TextBlock>具有項目<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>屬性設定。  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a>範例  
 設定對應<xref:System.Windows.TextTrimming>程式碼中的屬性以下所示。  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 目前三個選項的修剪文字： **CharacterEllipsis**， **WordEllipsis**，和**無**。  
  
 當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設**CharacterEllipsis**，修剪文字，再繼續使用省略符號在最接近的修剪邊緣的字元。  此設定是要修剪文字，使其更接近修剪界限，但可能會導致部分修剪文字。  下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>類似於上述定義的一個。  
  
 ![範例：TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")  
  
 當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設**WordEllipsis**，修剪文字，再繼續使用省略符號的修剪邊緣最接近的第一個完整單字的結尾。  此設定不會顯示部分修剪的文字的方式，但通常不是要修剪文字十分接近，修剪邊緣做為**CharacterEllipsis**設定。  下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>上面定義。  
  
 ![範例：TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")  
  
 當<xref:System.Windows.Controls.TextBlock.TextTrimming%2A>設**無**，會執行任何的文字修剪。  在此情況下，只會將文字裁剪到父文字容器的界限。  下圖顯示這項設定的效果<xref:System.Windows.Controls.TextBlock>類似於上述定義的一個。  
  
 ![範例：TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")
