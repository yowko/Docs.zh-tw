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
---
# <a name="how-to-hide-toolstripmenuitems"></a>如何：隱藏 ToolStripMenuItems
隱藏功能表項目是來控制您的應用程式的使用者介面，並限制使用者命令的方法。 通常，您要隱藏整個功能表，當所有在其上的功能表項目都無法使用。 這代表使用者的分心。 此外，您可能想要隱藏並停用功能表或功能表項目，如單獨隱藏不會阻止使用者使用快速鍵來存取功能表命令。  
  
### <a name="to-hide-any-menu-item-programmatically"></a>若要以程式設計方式隱藏任何功能表項目  
  
-   在方法中，您可以設定功能表項目的屬性，加入程式碼設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性`false`。  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [操作說明：停用 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)
