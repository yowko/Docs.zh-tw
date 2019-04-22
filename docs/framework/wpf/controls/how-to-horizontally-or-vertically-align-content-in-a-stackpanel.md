---
title: HOW TO：水平或垂直對齊 StackPanel 中的內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: 03348aa0eb5b6c1791c27683c1c6c6a5d4a8a9d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186039"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>HOW TO：水平或垂直對齊 StackPanel 中的內容
此範例示範如何調整<xref:System.Windows.Controls.StackPanel.Orientation%2A>內的內容<xref:System.Windows.Controls.StackPanel>項目，以及如何調整<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>和<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>子內容。  
  
## <a name="example"></a>範例  
 下列範例會建立三個<xref:System.Windows.Controls.ListBox>中的項目[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。 每個<xref:System.Windows.Controls.ListBox>代表的可能值<xref:System.Windows.Controls.StackPanel.Orientation%2A>， <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>，以及<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>的屬性<xref:System.Windows.Controls.StackPanel>。 當使用者選取的值中的任何<xref:System.Windows.Controls.ListBox>項目、 相關聯的屬性<xref:System.Windows.Controls.StackPanel>及其子<xref:System.Windows.Controls.Button>項目變更。  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 下列程式碼後置檔案會定義所做的變更相關聯的事件<xref:System.Windows.Controls.ListBox>選擇項目的變更。 <xref:System.Windows.Controls.StackPanel> 由<xref:System.Windows.FrameworkElement.Name%2A> `sp1`。  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [面板概觀](panels-overview.md)
