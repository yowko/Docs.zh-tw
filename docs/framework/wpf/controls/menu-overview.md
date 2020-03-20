---
title: 功能表概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 53bc8f10e61b6e4e9e1f3b9a484340d9e2ec2a85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186966"
---
# <a name="menu-overview"></a>功能表概觀
該<xref:System.Windows.Controls.Menu>類使您能夠按分層順序組織與命令和事件處理常式關聯的元素。 每個<xref:System.Windows.Controls.Menu>元素都包含元素的集合<xref:System.Windows.Controls.MenuItem>。  

<a name="menu_control"></a>
## <a name="menu-control"></a>功能表控制項  
 該<xref:System.Windows.Controls.Menu>控制項顯示指定應用程式的命令或選項的項清單。 通常，按一下<xref:System.Windows.Controls.MenuItem>將打開子功能表或導致應用程式執行命令。  
  
<a name="creating_menus"></a>
## <a name="creating-menus"></a>建立功能表  
 下面的示例創建 一<xref:System.Windows.Controls.Menu>個 用於操作<xref:System.Windows.Controls.TextBox>中的文本。 <xref:System.Windows.Controls.Menu>包含<xref:System.Windows.Controls.MenuItem>使用<xref:System.Windows.Controls.MenuItem.Command%2A>、<xref:System.Windows.Controls.MenuItem.IsCheckable%2A>和<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性 以及<xref:System.Windows.Controls.MenuItem.Checked>和<xref:System.Windows.Controls.MenuItem.Unchecked>和<xref:System.Windows.Controls.MenuItem.Click>事件的物件。  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>
## <a name="menuitems-with-keyboard-shortcuts"></a>具有鍵盤快速鍵的 MenuItem  
 鍵盤快速鍵是可以使用鍵盤輸入以調用<xref:System.Windows.Controls.Menu>命令的字元組合。 例如，「複製」**** 的快速鍵是 CTRL+C。 有兩個屬性可用於鍵盤快速鍵和功能表項目 -<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>或<xref:System.Windows.Controls.MenuItem.Command%2A>。  
  
<a name="menus_inputgesturetext"></a>
### <a name="inputgesturetext"></a>InputGestureText  
 下面的示例演示如何使用 屬性<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>將鍵盤快捷文本分配給<xref:System.Windows.Controls.MenuItem>控制項。 這只會將鍵盤快速鍵放在功能表項目中。  它不將命令與 相關聯<xref:System.Windows.Controls.MenuItem>。 應用程式必須處理使用者的輸入，才能執行動作。  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>
### <a name="command"></a>Command  
 下面的示例<xref:System.Windows.Controls.MenuItem.Command%2A>演示如何使用 屬性將 **"打開**"和"**保存"** 命令與<xref:System.Windows.Controls.MenuItem>控制項相關聯。 命令屬性不僅將命令與<xref:System.Windows.Controls.MenuItem>相關聯，而且還提供用作快捷方式的輸入手勢文本。  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 類<xref:System.Windows.Controls.MenuItem>還具有一個<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>屬性，該屬性指定發生命令的元素。 如果未<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>設置，具有鍵盤焦點的元素將接收該命令。 如需有關命令的詳細資訊，請參閱[命令概觀](../advanced/commanding-overview.md)。  
  
<a name="menu_styling"></a>
## <a name="menu-styling"></a>功能表樣式設定  
 使用控制項樣式，您可以顯著更改<xref:System.Windows.Controls.Menu>控制項的外觀和行為，而無需編寫自訂控制項。 除了設置可視屬性外，還可以<xref:System.Windows.Style>將 應用於控制項的各個部分、通過屬性更改控制項各部分的行為、添加其他部分或更改控制項的佈局。 以下示例演示了向<xref:System.Windows.Style><xref:System.Windows.Controls.Menu>控制項添加 的幾種方法。  
  
 第一個代碼示例定義一<xref:System.Windows.Style>個`Simple`調用，該調用示例演示如何在樣式中使用當前系統設置。 此程式碼指派 `MenuHighlightBrush` 的色彩作為功能表的背景色彩，以及 `MenuTextBrush` 作為功能表的前景色彩。 請注意，您需使用資源索引鍵來指派筆刷。  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 以下示例使用<xref:System.Windows.Trigger>元素，以便更改 的外觀<xref:System.Windows.Controls.MenuItem>以回應 在 上發生的事件。 <xref:System.Windows.Controls.Menu> 將滑鼠移到 上<xref:System.Windows.Controls.Menu>時，功能表項目的前景顏色和字體特徵將發生變化。  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>另請參閱

- [WPF 控制項陳列庫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
