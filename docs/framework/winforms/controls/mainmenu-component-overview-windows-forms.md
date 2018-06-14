---
title: MainMenu 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: a7ea9fcf25942f21d2d549ea998161398fbc608f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534208"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu 元件概觀 (Windows Form)
> [!IMPORTANT]
>  雖然<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>取代，並將功能加入至<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>的舊版中，控制項<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>您選擇保留的回溯相容性及供未來使用。  
  
 Windows Form<xref:System.Windows.Forms.MainMenu>元件會在執行階段顯示的功能表。 所有的個別項目與主功能表的子功能表卻<xref:System.Windows.Forms.MenuItem>物件。  
  
## <a name="key-properties"></a>索引鍵內容  
 功能表項目可以指定為預設項目，藉由設定<xref:System.Windows.Forms.MenuItem.DefaultItem%2A>屬性`true`。 在按下功能表時以粗體文字顯示的預設項目。 功能表項目的<xref:System.Windows.Forms.MenuItem.Checked%2A>屬性`true`或`false`，並指出是否已選取功能表項目。 功能表項目的<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>屬性自訂選取之項目的外觀： 如果<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>設`true`，選項按鈕旁邊的項目; 如果<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>設`false`，項目旁邊的核取記號會出現。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MainMenu>  
 <xref:System.Windows.Forms.Menu>  
 <xref:System.Windows.Forms.MenuItem>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
