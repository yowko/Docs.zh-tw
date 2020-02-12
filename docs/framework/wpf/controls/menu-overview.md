---
title: 功能表概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 3d5cfba0734e684349f7d73b7242f4b69089b94d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124646"
---
# <a name="menu-overview"></a>功能表概觀
<xref:System.Windows.Controls.Menu> 類別可讓您以階層順序組織與命令和事件處理常式相關聯的元素。 每個 <xref:System.Windows.Controls.Menu> 元素都包含 <xref:System.Windows.Controls.MenuItem> 元素的集合。  

<a name="menu_control"></a>   
## <a name="menu-control"></a>功能表控制項  
 [<xref:System.Windows.Controls.Menu>] 控制項會顯示指定應用程式之命令或選項的專案清單。 一般來說，按一下 <xref:System.Windows.Controls.MenuItem> 會開啟子功能表，或讓應用程式執行命令。  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>建立功能表  
 下列範例會建立 <xref:System.Windows.Controls.Menu> 來操作 <xref:System.Windows.Controls.TextBox>中的文字。 <xref:System.Windows.Controls.Menu> 包含使用 <xref:System.Windows.Controls.MenuItem.Command%2A>、<xref:System.Windows.Controls.MenuItem.IsCheckable%2A>和 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 屬性以及 <xref:System.Windows.Controls.MenuItem.Checked>、<xref:System.Windows.Controls.MenuItem.Unchecked>和 <xref:System.Windows.Controls.MenuItem.Click> 事件的 <xref:System.Windows.Controls.MenuItem> 物件。  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>具有鍵盤快速鍵的 MenuItem  
 鍵盤快速鍵是可以使用鍵盤輸入的字元組合，以叫用 <xref:System.Windows.Controls.Menu> 命令。 例如，「複製」的快速鍵是 CTRL+C。 有兩個屬性可用於鍵盤快速鍵和功能表項目，<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> 或 <xref:System.Windows.Controls.MenuItem.Command%2A>。  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 下列範例顯示如何使用 <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> 屬性，將鍵盤快速鍵文字指派給 <xref:System.Windows.Controls.MenuItem> 控制項。 這只會將鍵盤快速鍵放在功能表項目中。  它不會將命令與 <xref:System.Windows.Controls.MenuItem>產生關聯。 應用程式必須處理使用者的輸入，才能執行動作。  
  
 [!code-xaml[MenuEvent#6](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>命令  
 下列範例示範如何使用 [<xref:System.Windows.Controls.MenuItem.Command%2A>] 屬性，將 [**開啟**] 和 [**儲存**] 命令與 <xref:System.Windows.Controls.MenuItem> 控制項產生關聯。 命令屬性不僅會將命令與 <xref:System.Windows.Controls.MenuItem>產生關聯，還會提供輸入手勢文字做為快捷方式使用。  
  
 [!code-xaml[MenuEvent#8](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem> 類別也具有 <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> 屬性，它會指定命令發生所在的元素。 如果未設定 <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>，則具有鍵盤焦點的元素會接收命令。 如需有關命令的詳細資訊，請參閱[命令概觀](../advanced/commanding-overview.md)。  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>功能表樣式設定  
 使用控制項樣式，您可以大幅變更 <xref:System.Windows.Controls.Menu> 控制項的外觀和行為，而不需要撰寫自訂控制項。 除了設定視覺屬性之外，您也可以將 <xref:System.Windows.Style> 套用至控制項的個別部分、透過屬性變更控制項部分的行為，或加入其他元件或變更控制項的版面配置。 下列範例示範數種將 <xref:System.Windows.Style> 新增至 <xref:System.Windows.Controls.Menu> 控制項的方式。  
  
 第一個程式碼範例會定義稱為 `Simple` 的 <xref:System.Windows.Style>，以示範如何在樣式中使用目前的系統設定。 此程式碼指派 `MenuHighlightBrush` 的色彩作為功能表的背景色彩，以及 `MenuTextBrush` 作為功能表的前景色彩。 請注意，您需使用資源索引鍵來指派筆刷。  
  
 [!code-xaml[MenuStylesSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 下列範例會使用 <xref:System.Windows.Trigger> 元素，讓您變更 <xref:System.Windows.Controls.MenuItem> 的外觀，以回應發生在 <xref:System.Windows.Controls.Menu>上的事件。 當您將滑鼠游標移到 [<xref:System.Windows.Controls.Menu>] 上方時，功能表項目的前景色彩和字型特性也會變更。  
  
 [!code-xaml[MenuStylesSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>另請參閱

- [WPF 控制項陳列庫範例](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
