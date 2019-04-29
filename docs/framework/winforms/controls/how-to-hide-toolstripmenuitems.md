---
title: HOW TO：隱藏 ToolStripMenuItems
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: dc9daa945f2a546548f2cc6ea033378bd9ceff93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941216"
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="6139e-102">HOW TO：隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="6139e-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="6139e-103">隱藏功能表項目是用來控制您的應用程式的使用者介面，並限制使用者命令。</span><span class="sxs-lookup"><span data-stu-id="6139e-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="6139e-104">通常，您要隱藏整個功能表無法使用時，所有在其上的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="6139e-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="6139e-105">這代表使用者分心。</span><span class="sxs-lookup"><span data-stu-id="6139e-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="6139e-106">此外，您可能想要隱藏和停用功能表或功能表項目，為單獨的隱藏不會防止使用者使用攠摝坫存取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="6139e-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="6139e-107">若要以程式設計方式隱藏任何功能表項目</span><span class="sxs-lookup"><span data-stu-id="6139e-107">To hide any menu item programmatically</span></span>  
  
- <span data-ttu-id="6139e-108">在方法中您用來設定功能表項目的屬性，加入程式碼以設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="6139e-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6139e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6139e-109">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [<span data-ttu-id="6139e-110">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="6139e-110">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="6139e-111">如何：停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="6139e-111">How to: Disable ToolStripMenuItems</span></span>](how-to-disable-toolstripmenuitems.md)
