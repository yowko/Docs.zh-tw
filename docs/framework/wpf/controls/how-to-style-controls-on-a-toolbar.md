---
title: 如何：工具列上的樣式控制項
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: 78b9fc505c3c9045a0ca16ddaa1361c90bcc896a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459414"
---
# <a name="how-to-style-controls-on-a-toolbar"></a>如何：工具列上的樣式控制項
<xref:System.Windows.Controls.ToolBar> 會定義 <xref:System.Windows.ResourceKey> 物件，以便在 <xref:System.Windows.Controls.ToolBar>內指定控制項的樣式。  若要在 <xref:System.Windows.Controls.ToolBar>中設定控制項的樣式，請將樣式的 `x:key` 屬性設為 <xref:System.Windows.Controls.ToolBar>中定義的 <xref:System.Windows.ResourceKey>。  
  
 <xref:System.Windows.Controls.ToolBar> 會定義下列 <xref:System.Windows.ResourceKey> 物件：  
  
- <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a>範例  
 下列範例會定義 <xref:System.Windows.Controls.ToolBar>內控制項的樣式。  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>請參閱

- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
