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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332179"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="79d8f-102">HOW TO：使用 Windows Forms ContextMenu 元件新增和移除功能表項目</span><span class="sxs-lookup"><span data-stu-id="79d8f-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="79d8f-103">說明如何新增和移除 Windows Form 中的捷徑功能表項目。</span><span class="sxs-lookup"><span data-stu-id="79d8f-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="79d8f-104">Windows Form<xref:System.Windows.Forms.ContextMenu>元件提供給所選物件相關的常用命令的功能表。</span><span class="sxs-lookup"><span data-stu-id="79d8f-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="79d8f-105">您也可以加入至捷徑功能表新增項目<xref:System.Windows.Forms.MenuItem>物件至<xref:System.Windows.Forms.Menu.MenuItems%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="79d8f-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="79d8f-106">您可以永久移除項目從快顯功能表;不過，在執行階段可能更適合隱藏，或改為停用項目。</span><span class="sxs-lookup"><span data-stu-id="79d8f-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="79d8f-107">雖然<xref:System.Windows.Forms.MenuStrip>並<xref:System.Windows.Forms.ContextMenuStrip>取代及新增功能<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>控制項的舊版本中，<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>會保留回溯相容性以及供未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="79d8f-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="79d8f-108">若要移除的快顯功能表中的項目</span><span class="sxs-lookup"><span data-stu-id="79d8f-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="79d8f-109">使用<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>或是<xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>方法<xref:System.Windows.Forms.Menu.MenuItems%2A>的集合<xref:System.Windows.Forms.ContextMenu>元件中移除特定的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="79d8f-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="79d8f-110">-或-</span><span class="sxs-lookup"><span data-stu-id="79d8f-110">-or-</span></span>  
  
2. <span data-ttu-id="79d8f-111">使用`Clear`方法`MenuItems`的集合<xref:System.Windows.Forms.ContextMenu>元件，以移除 [] 功能表中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="79d8f-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="79d8f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79d8f-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="79d8f-113">ContextMenu 元件</span><span class="sxs-lookup"><span data-stu-id="79d8f-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="79d8f-114">ContextMenu 元件概觀</span><span class="sxs-lookup"><span data-stu-id="79d8f-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
