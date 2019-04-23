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
ms.openlocfilehash: da1b76a7019f364e7463a8345aa80d9a9bd6089e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168476"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu 元件概觀 (Windows Form)
> [!IMPORTANT]
>  雖然<xref:System.Windows.Forms.MenuStrip>並<xref:System.Windows.Forms.ContextMenuStrip>取代及新增功能<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>控制項的舊版本中，<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>會保留回溯相容性以及供未來使用，如果您選擇。  
  
 Windows Form<xref:System.Windows.Forms.MainMenu>元件會在執行階段顯示功能表。 所有的個別項目與主功能表的子功能表卻<xref:System.Windows.Forms.MenuItem>物件。  
  
## <a name="key-properties"></a>索引鍵內容  
 功能表項目可以指定為預設的項目，藉由設定<xref:System.Windows.Forms.MenuItem.DefaultItem%2A>屬性設`true`。 按一下 [] 功能表時以粗體文字顯示預設項目。 功能表項目的<xref:System.Windows.Forms.MenuItem.Checked%2A>屬性是`true`或`false`，並指出是否已選取功能表項目。 功能表項目的<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>屬性自訂所選取項目的外觀： 如果<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>設為`true`，選項按鈕旁邊的項目; 如果<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>設定為`false`，項目旁的核取記號隨即出現。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
