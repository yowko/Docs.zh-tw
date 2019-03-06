---
title: HOW TO：調整段落之間的間距
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367475"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>HOW TO：調整段落之間的間距
此範例示範如何調整或排除在非固定格式內容中的段落之間的間距。  
  
 在非固定格式內容中顯示段落之間的額外空間是這些段落; 上設定的邊界的結果因此，可以藉由調整邊界的段落控制段落之間的間距。  若要完全排除這兩個段落的額外間距，設定 針對至段落的邊界**0**。  若要達到統一整個段落之間的間距<xref:System.Windows.Documents.FlowDocument>，使用設為統一的邊界值中的所有段落的樣式<xref:System.Windows.Documents.FlowDocument>。  
  
 請務必注意，兩個相鄰的段落的邊界會 「 摺疊 」 到較大的兩個邊界，而非向上加倍。 因此，如果兩個相鄰的段落會分別有 20 個像素和 40 像素的邊界，段落之間產生的空間會是 40 像素，較大的兩個邊界值。  
  
## <a name="example"></a>範例  
 下列範例會使用樣式來設定所有邊界<xref:System.Windows.Documents.Paragraph>中的項目<xref:System.Windows.Documents.FlowDocument>要**0**，這便能有效去除在段落之間的額外間距<xref:System.Windows.Documents.FlowDocument>。  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
