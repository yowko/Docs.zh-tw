---
title: HOW TO：處理 ScrollChanged 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], raising ScrollChanged events
- ScrollChanged events [WPF]
ms.assetid: 42c695d8-ee28-49d4-80fd-fc71e9be7f29
ms.openlocfilehash: b38effc9e32a5d13a0556b345bc0be25e81e0036
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711742"
---
# <a name="how-to-handle-the-scrollchanged-event"></a>HOW TO：處理 ScrollChanged 事件
## <a name="example"></a>範例  
 此範例示範如何處理<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>事件的<xref:System.Windows.Controls.ScrollViewer>。  
  
 A<xref:System.Windows.Documents.FlowDocument>具有項目<xref:System.Windows.Documents.Paragraph>中所定義的組件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 當<xref:System.Windows.Controls.ScrollViewer.ScrollChanged>因為使用者互動就會發生事件，會叫用處理常式，並寫入文字<xref:System.Windows.Controls.TextBlock>指出事件已發生。  
  
 [!code-xaml[scrollchangedeventargsLayout#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#1)]  
[!code-xaml[scrollchangedeventargsLayout#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[scrollchangedeventargsLayout#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/scrollchangedeventargsLayout/CSharp/Window1.xaml.cs#3)]
 [!code-vb[scrollchangedeventargsLayout#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/scrollchangedeventargsLayout/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.ScrollViewer.ScrollChanged>
- <xref:System.Windows.Controls.ScrollChangedEventHandler>
- <xref:System.Windows.Controls.ScrollChangedEventArgs>
