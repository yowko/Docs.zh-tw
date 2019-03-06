---
title: TextBlock 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
ms.openlocfilehash: a3ea656a902f8a112a700667b6e08cae7463f68d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374462"
---
# <a name="textblock-overview"></a>TextBlock 概觀
<xref:System.Windows.Controls.TextBlock>控制項提供的彈性文字支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。 這個元素的主要目標是不需要超過一個段落文字的基本 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 案例。 它支援一些屬性可讓準確控制呈現，例如<xref:System.Windows.Controls.TextBlock.FontFamily%2A>， <xref:System.Windows.Controls.TextBlock.FontSize%2A>， <xref:System.Windows.Controls.TextBlock.FontWeight%2A>， <xref:System.Windows.Controls.TextBlock.TextEffects%2A>，和<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>。 文字內容可以使用新增<xref:System.Windows.Controls.TextBlock.Text%2A>屬性。 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中使用時，開始和結束標記之間的內容會以隱含方式加入為元素的文字。  
  
 A<xref:System.Windows.Controls.TextBlock>項目可以具現化很簡單地使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xaml[TextBlockSnip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 同樣地，使用<xref:System.Windows.Controls.TextBlock>在程式碼中的項目是相當簡單。  
  
 [!code-csharp[TextBlockSnip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.Label>
