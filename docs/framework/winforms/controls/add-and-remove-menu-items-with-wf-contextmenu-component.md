---
title: 作法：使用 Windows Forms ContextMenu 元件新增和移除功能表項目
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
ms.openlocfilehash: 5d1862b1fc1398f0f8c2217b51c4efb93db639af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957025"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>HOW TO：使用 Windows Forms ContextMenu 元件新增和移除功能表項目
說明如何新增和移除 Windows Forms 中的快捷方式功能表項目。  
  
 [Windows Forms <xref:System.Windows.Forms.ContextMenu> ] 元件會提供與所選物件相關之常用命令的功能表。 您可以藉由將<xref:System.Windows.Forms.MenuItem>物件加入<xref:System.Windows.Forms.Menu.MenuItems%2A>至集合, 將專案新增至快捷方式功能表。  
  
 您可以永久移除快捷方式功能表中的專案;不過, 在執行時間, 可能更適合改為隱藏或停用專案。  
  
> [!IMPORTANT]
> 雖然<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenu>會取代並將功能加入舊版的和控制項, 但<xref:System.Windows.Forms.MainMenu>如果您選擇, 則會保留以供回溯相容性和未來使用。 <xref:System.Windows.Forms.ContextMenuStrip>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>若要從快捷方式功能表移除專案  
  
1. 使用元件集合的或<xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>方法 <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> <xref:System.Windows.Forms.Menu.MenuItems%2A> , 移除特定的功能表項目。 <xref:System.Windows.Forms.ContextMenu>  
  
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
  
2. `MenuItems`使用元件集合的方法, 移除功能表中的所有專案。 `Clear` <xref:System.Windows.Forms.ContextMenu>  
  
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
