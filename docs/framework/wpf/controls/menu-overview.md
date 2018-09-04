---
title: 功能表概觀
ms.date: 03/30/2017
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
ms.openlocfilehash: a1074d09c195a78dcc79df0841123672b716bcfe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536420"
---
# <a name="menu-overview"></a>功能表概觀
<xref:System.Windows.Controls.Menu>類別可讓您組織與命令和事件處理常式，以階層順序相關聯的項目。 每個<xref:System.Windows.Controls.Menu>項目包含集合<xref:System.Windows.Controls.MenuItem>項目。  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>功能表控制項  
 <xref:System.Windows.Controls.Menu>控制項顯示的清單，這些項目指定命令或應用程式的選項。 一般而言，按一下<xref:System.Windows.Controls.MenuItem>開啟子功能表，或讓應用程式執行命令。  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>建立功能表  
 下列範例會建立<xref:System.Windows.Controls.Menu>中的文字操作<xref:System.Windows.Controls.TextBox>。 <xref:System.Windows.Controls.Menu>包含<xref:System.Windows.Controls.MenuItem>物件，使用<xref:System.Windows.Controls.MenuItem.Command%2A>， <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>，並<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>屬性和<xref:System.Windows.Controls.MenuItem.Checked>， <xref:System.Windows.Controls.MenuItem.Unchecked>，以及<xref:System.Windows.Controls.MenuItem.Click>事件。  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>具有鍵盤快速鍵的 MenuItem  
 鍵盤快速鍵是字元組合，可以透過叫用鍵盤輸入<xref:System.Windows.Controls.Menu>命令。 例如，「複製」的快速鍵是 CTRL+C。 鍵盤快速鍵和功能表項目可以使用兩個屬性 —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>或<xref:System.Windows.Controls.MenuItem.Command%2A>。  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 下列範例示範如何使用<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>要指派到的鍵盤快速鍵文字內容<xref:System.Windows.Controls.MenuItem>控制項。 這只會將鍵盤快速鍵放在功能表項目中。  它不會將關聯的命令與<xref:System.Windows.Controls.MenuItem>。 應用程式必須處理使用者的輸入，才能執行動作。  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>命令  
 下列範例示範如何使用<xref:System.Windows.Controls.MenuItem.Command%2A>產生關聯的屬性**開放**並**儲存**命令搭配<xref:System.Windows.Controls.MenuItem>控制項。 命令屬性不僅關聯的命令<xref:System.Windows.Controls.MenuItem>，還會提供要用來作為快速鍵的輸入的手勢文字。  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem>類別也有<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>屬性，指定命令發生所在的項目。 如果<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>未設定，具有鍵盤焦點的項目會在接收命令。 如需有關命令的詳細資訊，請參閱[命令概觀](../../../../docs/framework/wpf/advanced/commanding-overview.md)。  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>功能表樣式設定  
 使用控制項樣式設定，您可以大幅變更的外觀和行為<xref:System.Windows.Controls.Menu>而不需要撰寫自訂控制項的控制項。 除了設定視覺屬性，您也可以套用<xref:System.Windows.Style>的控制項的個別組件，變更屬性，透過控制項的組件的行為或新增其他組件或變更控制項的配置。 下列範例示範數種方式可以新增<xref:System.Windows.Style>至<xref:System.Windows.Controls.Menu>控制項。  
  
 第一個程式碼範例會定義<xref:System.Windows.Style>稱為`Simple`示範如何使用目前的系統設定，以您的樣式。 此程式碼指派 `MenuHighlightBrush` 的色彩作為功能表的背景色彩，以及 `MenuTextBrush` 作為功能表的前景色彩。 請注意，您需使用資源索引鍵來指派筆刷。  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 下列範例會使用<xref:System.Windows.Trigger>可讓您變更外觀的項目<xref:System.Windows.Controls.MenuItem>中所發生的事件回應<xref:System.Windows.Controls.Menu>。 當您將滑鼠指標移<xref:System.Windows.Controls.Menu>，前景色彩和字型特性功能表項目的變更。  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>另請參閱  
 [WPF 控制項陳列庫範例](https://go.microsoft.com/fwlink/?LinkID=160053)
