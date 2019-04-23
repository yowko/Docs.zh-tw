---
title: HOW TO：使用 ScrollViewer 的內容捲動方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: e81c63de16d09de8435d5ec49a013bf8dc5927cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142151"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>HOW TO：使用 ScrollViewer 的內容捲動方法
此範例示範如何使用捲動方法<xref:System.Windows.Controls.ScrollViewer>項目。 這些方法會提供累加捲動內容的列或頁面上，在<xref:System.Windows.Controls.ScrollViewer>。  
  
## <a name="example"></a>範例  
 下列範例會建立<xref:System.Windows.Controls.ScrollViewer>名為`sv1`，其中裝載子系<xref:System.Windows.Controls.TextBlock>項目。 因為<xref:System.Windows.Controls.TextBlock>大於父代<xref:System.Windows.Controls.ScrollViewer>，捲軸出現，以啟用捲動功能。 <xref:System.Windows.Controls.Button> 在個別左側停駐項目代表各種捲動方法<xref:System.Windows.Controls.StackPanel>。 每個<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案會呼叫相關的自訂方法可控制捲動行為中的<xref:System.Windows.Controls.ScrollViewer>。  
  
 [!code-xaml[ScrollViewerMethods#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 下列範例會使用<xref:System.Windows.Controls.ScrollViewer.LineUp%2A>和<xref:System.Windows.Controls.ScrollViewer.LineDown%2A>方法。  
  
 [!code-csharp[ScrollViewerMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
