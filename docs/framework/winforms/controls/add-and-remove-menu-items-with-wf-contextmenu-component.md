---
title: 如何：使用 Windows Form ContextMenu 元件加入和移除功能表項目
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
ms.openlocfilehash: 7cc11eaf4a671c76933c2705b41a4df6c35c0536
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524725"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>如何：使用 Windows Form ContextMenu 元件加入和移除功能表項目
說明如何新增及移除 Windows Form 中的捷徑功能表項目。  
  
 Windows Form<xref:System.Windows.Forms.ContextMenu>元件提供與所選物件相關的常用命令的功能表。 您也可以新增的快顯功能表加入項目<xref:System.Windows.Forms.MenuItem>物件加入至<xref:System.Windows.Forms.Menu.MenuItems%2A>集合。  
  
 您可以永久移除項目從快顯功能表。不過，在執行階段，它可能會更加適合來隱藏或停用而項目。  
  
> [!IMPORTANT]
>  雖然<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>取代，並將功能加入至<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>的舊版中，控制項<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>您選擇保留的回溯相容性及供未來使用。  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>若要移除的快顯功能表中的項目  
  
1.  使用<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>或<xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>方法<xref:System.Windows.Forms.Menu.MenuItems%2A>集合<xref:System.Windows.Forms.ContextMenu>元件中移除特定的功能表項目。  
  
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
  
2.  使用`Clear`方法`MenuItems`集合<xref:System.Windows.Forms.ContextMenu>元件從功能表中移除所有項目。  
  
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
 <xref:System.Windows.Forms.ContextMenu>  
 [ContextMenu 元件](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)  
 [ContextMenu 元件概觀](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)
