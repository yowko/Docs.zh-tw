---
title: 功能表概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: 4c3e8398ad058c50df535fea88dd9f366b7f24ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="menu-overview"></a>功能表概觀
<xref:System.Windows.Controls.Menu>類別可讓您組織命令和事件處理常式，以階層順序相關聯的項目。 每個<xref:System.Windows.Controls.Menu>項目包含集合<xref:System.Windows.Controls.MenuItem>項目。  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>功能表控制項  
 <xref:System.Windows.Controls.Menu>控制項呈現的項目，指定命令或應用程式的選項清單。 一般而言，按一下<xref:System.Windows.Controls.MenuItem>開啟子功能表，或是造成應用程式來執行命令。  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>建立功能表  
 下列範例會建立<xref:System.Windows.Controls.Menu>操作中的文字<xref:System.Windows.Controls.TextBox>。 <xref:System.Windows.Controls.Menu>包含<xref:System.Windows.Controls.MenuItem>物件使用<xref:System.Windows.Controls.MenuItem.Command%2A>， <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>，和<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性和<xref:System.Windows.Controls.MenuItem.Checked>， <xref:System.Windows.Controls.MenuItem.Unchecked>，和<xref:System.Windows.Controls.MenuItem.Click>事件。  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>具有鍵盤快速鍵的 MenuItem  
 鍵盤快速鍵是您可以用來叫用鍵盤輸入的字元組合<xref:System.Windows.Controls.Menu>命令。 例如，「複製」的快速鍵是 CTRL+C。 有兩個屬性，若要使用鍵盤快速鍵與功能表項目-<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>或<xref:System.Windows.Controls.MenuItem.Command%2A>。  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 下列範例示範如何使用<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>要指派到的鍵盤快速鍵文字內容<xref:System.Windows.Controls.MenuItem>控制項。 這只會將鍵盤快速鍵放在功能表項目中。  不將關聯命令與<xref:System.Windows.Controls.MenuItem>。 應用程式必須處理使用者的輸入，才能執行動作。  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>命令  
 下列範例示範如何使用<xref:System.Windows.Controls.MenuItem.Command%2A>相關聯屬性**開啟**和**儲存**命令搭配<xref:System.Windows.Controls.MenuItem>控制項。 命令內容不只關聯的命令<xref:System.Windows.Controls.MenuItem>，但它也提供了使用較快速的輸入的動作文字。  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem>類別也有<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>屬性，指定命令的發生位置的項目。 如果<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>未設定，具有鍵盤焦點的項目會在接收命令。 如需有關命令的詳細資訊，請參閱[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>功能表樣式設定  
 控制項的樣式，您可以利用大幅變更外觀和行為<xref:System.Windows.Controls.Menu>而不需要撰寫自訂控制項的控制項。 除了設定視覺內容，您也可以套用<xref:System.Windows.Style>個別部分控制項的詳細資訊，變更行為的屬性，透過控制項的部分或將其他組件加入或變更控制項的配置。 下列範例將示範數個方法可以加入<xref:System.Windows.Style>至<xref:System.Windows.Controls.Menu>控制項。  
  
 第一個程式碼範例會定義<xref:System.Windows.Style>呼叫`Simple`，示範如何使用目前的系統設定，在您的風格。 此程式碼指派 `MenuHighlightBrush` 的色彩作為功能表的背景色彩，以及 `MenuTextBrush` 作為功能表的前景色彩。 請注意，您需使用資源索引鍵來指派筆刷。  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 下列範例會使用<xref:System.Windows.Trigger>項目可讓您變更的外觀<xref:System.Windows.Controls.MenuItem>所發生的事件回應<xref:System.Windows.Controls.Menu>。 當您將滑鼠移<xref:System.Windows.Controls.Menu>的前景色彩和字型特性功能表項目的變更。  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>另請參閱  
 [WPF 控制項陳列庫範例](http://go.microsoft.com/fwlink/?LinkID=160053)
