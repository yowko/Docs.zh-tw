---
title: 如何：使用 ScrollViewer 建立 Expander
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
ms.openlocfilehash: 6c014d4f6a12bfb58c2ae68f580f632c9478c82f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>如何：使用 ScrollViewer 建立 Expander
這個範例示範如何建立<xref:System.Windows.Controls.Expander>包含複雜的內容，例如影像和文字控制項。 此範例也內含的之內容<xref:System.Windows.Controls.Expander>中<xref:System.Windows.Controls.ScrollViewer>控制項。  
  
## <a name="example"></a>範例  
 下列範例示範如何建立<xref:System.Windows.Controls.Expander>。 此範例會使用<xref:System.Windows.Controls.Primitives.BulletDecorator>控制項，包含影像和文字，以定義<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>。 A<xref:System.Windows.Controls.ScrollViewer>控制項提供一種方法捲動展開的內容。  
  
 請注意，範例會設定<xref:System.Windows.FrameworkElement.Height%2A>屬性<xref:System.Windows.Controls.ScrollViewer>而不是內容。 如果<xref:System.Windows.FrameworkElement.Height%2A>設定於內容，<xref:System.Windows.Controls.ScrollViewer>不允許使用者捲動內容。 <xref:System.Windows.FrameworkElement.Width%2A>上設定屬性<xref:System.Windows.Controls.Expander>控制項與此設定適用於<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和展開的內容。  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Expander>  
 [Expander 概觀](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
