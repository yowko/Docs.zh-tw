---
title: HOW TO：停用 ToolStripMenuItems
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046217"
---
# <a name="how-to-disable-toolstripmenuitems"></a>作法：停用 ToolStripMenuItems
您可以啟用和停用功能表項目以回應使用者活動, 以限制或放寬使用者可能進行的命令。 建立功能表項目時, 預設會啟用這些專案, 但可透過<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性來調整。 您可以在設計階段于 [**屬性**] 視窗中操作這個屬性, 或是在程式碼中設定它以程式設計方式。  
  
### <a name="to-disable-a-menu-item-programmatically"></a>以程式設計方式停用功能表項目  
  
- 在您設定功能表項目屬性的方法中, 加入程式碼以將<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性設定為。 `false`  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    > 停用功能表中的第一個或最上層功能表項目, 會隱藏功能表中包含的所有功能表項目, 但不會停用它們。 同樣地, 停用具有子功能表專案的功能表項目會隱藏子功能表專案, 但不會停用它們。 如果指定功能表上的所有命令都無法供使用者使用, 就會被視為良好的程式設計實務, 可以隱藏和停用整個功能表, 因為這會呈現全新的使用者介面。 您應該隱藏和停用功能表, 並停用功能表中的每個專案和子功能表專案, 因為單獨隱藏並不會阻止透過快速鍵存取功能表命令。 將最上層功能表項目的`false` 屬性設定為,以隱藏整個功能表。<xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [如何：隱藏 ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
