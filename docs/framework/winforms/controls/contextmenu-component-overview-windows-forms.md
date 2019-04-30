---
title: ContextMenu 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956048"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu 元件概觀 (Windows Form)
> [!IMPORTANT]
>  雖然<xref:System.Windows.Forms.MenuStrip>並<xref:System.Windows.Forms.ContextMenuStrip>取代及新增功能<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>控制項的舊版本中，<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>會保留回溯相容性以及供未來使用，如果您選擇。  
  
 使用 Windows Form<xref:System.Windows.Forms.ContextMenu>元件，您可以提供使用者更容易存取的快顯功能表與所選物件相關聯的常用命令。 快顯功能表中的項目通常是從主應用程式中其他地方出現的功能表項目的子集。 使用者可以按一下滑鼠右鍵，通常存取捷徑功能表。 在 Windows Forms 上快顯功能表會與控制項相關聯。  
  
## <a name="key-properties"></a>索引鍵內容  
 您可以與控制項關聯的捷徑功能表，設定控制項的<xref:System.Windows.Forms.Control.ContextMenu%2A>屬性設<xref:System.Windows.Forms.ContextMenu>元件。 單一的捷徑功能表可以與多個控制項，相關聯，但每個控制項都可以有只有一個快顯功能表。  
  
 索引鍵內容<xref:System.Windows.Forms.ContextMenu>元件是<xref:System.Windows.Forms.Menu.MenuItems%2A>屬性。 您可以新增功能表項目以程式設計方式建立<xref:System.Windows.Forms.MenuItem>物件，並將它們加入至<xref:System.Windows.Forms.Menu.MenuItemCollection>的快顯功能表。 快顯功能表中的項目通常取自其他功能表中，因為您將複製它們，以最常加入至捷徑功能表項目。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
