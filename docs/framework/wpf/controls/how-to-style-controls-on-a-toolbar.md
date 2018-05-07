---
title: 如何：工具列上的樣式控制項
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: cc5ac9dd64072c34ff999255a27dd92f311cda0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-style-controls-on-a-toolbar"></a>如何：工具列上的樣式控制項
<xref:System.Windows.Controls.ToolBar>定義<xref:System.Windows.ResourceKey>物件，指定控制項內的樣式<xref:System.Windows.Controls.ToolBar>。  若要設定在控制項的樣式<xref:System.Windows.Controls.ToolBar>，將`x:key`要的樣式屬性<xref:System.Windows.ResourceKey>中定義<xref:System.Windows.Controls.ToolBar>。  
  
 <xref:System.Windows.Controls.ToolBar>會定義下列<xref:System.Windows.ResourceKey>物件：  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a>範例  
 下列範例會定義內控制項的樣式<xref:System.Windows.Controls.ToolBar>。  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>另請參閱  
 [樣式設定和範本化](../../../../docs/framework/wpf/controls/styling-and-templating.md)
