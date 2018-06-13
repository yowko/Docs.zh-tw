---
title: 如何：隱藏 ToolStripMenuItems
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
ms.openlocfilehash: 73f67bbe6b2d51a59b6f72ab5faf21db9d6db12d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531949"
---
# <a name="how-to-hide-toolstripmenuitems"></a><span data-ttu-id="c4aba-102">如何：隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="c4aba-102">How to: Hide ToolStripMenuItems</span></span>
<span data-ttu-id="c4aba-103">隱藏功能表項目是來控制您的應用程式的使用者介面，並限制使用者命令的方法。</span><span class="sxs-lookup"><span data-stu-id="c4aba-103">Hiding menu items is a way to control the user interface of your application and restrict user commands.</span></span> <span data-ttu-id="c4aba-104">通常，您要隱藏整個功能表，當所有在其上的功能表項目都無法使用。</span><span class="sxs-lookup"><span data-stu-id="c4aba-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="c4aba-105">這代表使用者的分心。</span><span class="sxs-lookup"><span data-stu-id="c4aba-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="c4aba-106">此外，您可能想要隱藏並停用功能表或功能表項目，如單獨隱藏不會阻止使用者使用快速鍵來存取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="c4aba-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span>  
  
### <a name="to-hide-any-menu-item-programmatically"></a><span data-ttu-id="c4aba-107">若要以程式設計方式隱藏任何功能表項目</span><span class="sxs-lookup"><span data-stu-id="c4aba-107">To hide any menu item programmatically</span></span>  
  
-   <span data-ttu-id="c4aba-108">在方法中，您可以設定功能表項目的屬性，加入程式碼設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="c4aba-108">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c4aba-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4aba-109">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [<span data-ttu-id="c4aba-110">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="c4aba-110">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="c4aba-111">操作說明：停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="c4aba-111">How to: Disable ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
