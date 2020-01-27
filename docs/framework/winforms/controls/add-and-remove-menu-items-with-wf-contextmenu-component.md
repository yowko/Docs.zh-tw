---
title: 使用 CoNtextMenu 元件新增和移除功能表項目
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
ms.openlocfilehash: 989ab6d47ec761930a32f542b5fa1136e831f73d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746277"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>如何：使用 Windows Form ContextMenu 元件加入和移除功能表項目
說明如何新增和移除 Windows Forms 中的快捷方式功能表項目。  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> 元件會提供與所選物件相關之常用命令的功能表。 您可以藉由將 <xref:System.Windows.Forms.MenuItem> 物件加入至 <xref:System.Windows.Forms.Menu.MenuItems%2A> 集合，將專案新增至快捷方式功能表。  
  
 您可以永久移除快捷方式功能表中的專案;不過，在執行時間，可能更適合改為隱藏或停用專案。  
  
> [!IMPORTANT]
> 雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 將功能取代並加入舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但如果您選擇，<xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 會保留供回溯相容性及未來使用。  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>若要從快捷方式功能表移除專案  
  
1. 使用 <xref:System.Windows.Forms.ContextMenu> 元件之 <xref:System.Windows.Forms.Menu.MenuItems%2A> 集合的 <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> 或 <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> 方法，以移除特定的功能表項目。  
  
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
  
2. 使用 <xref:System.Windows.Forms.ContextMenu> 元件之 `MenuItems` 集合的 `Clear` 方法，從功能表中移除所有專案。  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ContextMenu>
- [ContextMenu 元件](contextmenu-component-windows-forms.md)
- [ContextMenu 元件概觀](contextmenu-component-overview-windows-forms.md)
