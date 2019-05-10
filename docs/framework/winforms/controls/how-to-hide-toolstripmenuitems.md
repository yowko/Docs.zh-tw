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
ms.openlocfilehash: 64c0f093063357c1e8db5933c035cc8295ad4f1e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623046"
---
# <a name="how-to-hide-toolstripmenuitems"></a>HOW TO：隱藏 ToolStripMenuItems
隱藏功能表項目是用來控制您的應用程式的使用者介面，並限制使用者命令。 通常，您要隱藏整個功能表無法使用時，所有在其上的功能表項目。 這代表使用者分心。 此外，您可能想要隱藏和停用功能表或功能表項目，為單獨的隱藏不會防止使用者使用攠摝坫存取功能表命令。  
  
### <a name="to-hide-any-menu-item-programmatically"></a>若要以程式設計方式隱藏任何功能表項目  
  
- 在方法中您用來設定功能表項目的屬性，加入程式碼以設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性設`false`。  
  
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

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
- [如何：停用 ToolStripMenuItems](how-to-disable-toolstripmenuitems.md)
