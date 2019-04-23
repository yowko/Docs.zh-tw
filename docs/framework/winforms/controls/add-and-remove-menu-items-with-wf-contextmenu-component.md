---
title: HOW TO：使用 Windows Forms ContextMenu 元件新增和移除功能表項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
ms.openlocfilehash: cf70a5cc426b6c6075d1deb11aa2685c39a065c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332179"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>HOW TO：使用 Windows Forms ContextMenu 元件新增和移除功能表項目
說明如何新增和移除 Windows Form 中的捷徑功能表項目。  
  
 Windows Form<xref:System.Windows.Forms.ContextMenu>元件提供給所選物件相關的常用命令的功能表。 您也可以加入至捷徑功能表新增項目<xref:System.Windows.Forms.MenuItem>物件至<xref:System.Windows.Forms.Menu.MenuItems%2A>集合。  
  
 您可以永久移除項目從快顯功能表;不過，在執行階段可能更適合隱藏，或改為停用項目。  
  
> [!IMPORTANT]
>  雖然<xref:System.Windows.Forms.MenuStrip>並<xref:System.Windows.Forms.ContextMenuStrip>取代及新增功能<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>控制項的舊版本中，<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>會保留回溯相容性以及供未來使用，如果您選擇。  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>若要移除的快顯功能表中的項目  
  
1. 使用<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>或是<xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>方法<xref:System.Windows.Forms.Menu.MenuItems%2A>的集合<xref:System.Windows.Forms.ContextMenu>元件中移除特定的功能表項目。  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     -或-  
  
2. 使用`Clear`方法`MenuItems`的集合<xref:System.Windows.Forms.ContextMenu>元件，以移除 [] 功能表中的所有項目。  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ContextMenu>
- [ContextMenu 元件](contextmenu-component-windows-forms.md)
- [ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)
