---
title: 如何：停用 ToolStripMenuItems
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
ms.openlocfilehash: 20d0e13642aac3004a31ff416318cf6723207379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-toolstripmenuitems"></a>如何：停用 ToolStripMenuItems
您可以限制或擴大使用者可能會進行啟用及停用功能表項目，以回應使用者活動的命令。 依預設會啟用功能表項目，建立，但這可以透過調整<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性。 您可以操作此屬性在設計階段於**屬性**視窗或以程式設計方式在程式碼中設定。  
  
### <a name="to-disable-a-menu-item-programmatically"></a>若要以程式設計的方式停用功能表項目  
  
-   在方法中，您可以設定功能表項目的屬性，加入程式碼設定<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性`false`。  
  
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
    >  停用功能表中的第一個或最上層功能表項目會隱藏包含功能表中的所有功能表項目，但不會停用它們。 同樣地，停用功能表項目具有子功能表項目會隱藏子功能表項目，但不會停用它們。 如果使用者無法使用指定的功能表上的所有命令，它會視為良好的程式設計作法，同時隱藏和停用整個功能表中，這會清除使用者介面。 您應該隱藏和停用功能表上，並停用每個項目和子功能表項目在功能表中，因為單獨隱藏並不會防止攠摝坫透過功能表命令的存取。 設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性的最上層功能表項目`false`隱藏整個功能表。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [操作說明：隱藏 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
