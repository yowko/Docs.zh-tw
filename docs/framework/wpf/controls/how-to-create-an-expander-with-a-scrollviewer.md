---
title: HOW TO：使用 ScrollViewer 建立 Expander
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 8d21c7ec0172dca23f218a0d710c3976872f162c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681959"
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>HOW TO：使用 ScrollViewer 建立 Expander
此範例示範如何建立<xref:System.Windows.Controls.Expander>包含複雜的內容，例如影像和文字的控制項。 此範例也會括住的內容<xref:System.Windows.Controls.Expander>在<xref:System.Windows.Controls.ScrollViewer>控制項。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立<xref:System.Windows.Controls.Expander>。 此範例會使用<xref:System.Windows.Controls.Primitives.BulletDecorator>控制項，包含影像和文字，以定義<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>。 A<xref:System.Windows.Controls.ScrollViewer>控制項提供方法來捲動展開的內容。  
  
 請注意，此範例會設定<xref:System.Windows.FrameworkElement.Height%2A>屬性上的<xref:System.Windows.Controls.ScrollViewer>而不是在內容上。 如果<xref:System.Windows.FrameworkElement.Height%2A>設定的內容，<xref:System.Windows.Controls.ScrollViewer>不允許使用者捲動內容。 <xref:System.Windows.FrameworkElement.Width%2A>上設定屬性<xref:System.Windows.Controls.Expander>控制項，此設定適用於<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和展開的內容。  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.Expander>
- [Expander 概觀](../../../../docs/framework/wpf/controls/expander-overview.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
