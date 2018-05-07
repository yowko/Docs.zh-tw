---
title: 如何：移動 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: 5cfaf87a59d27678cfb786633ed4c9a9f66bac76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-move-toolstripmenuitems"></a>如何：移動 ToolStripMenuItems
在設計階段，您可以移動整個最上層功能表和其功能表項目不同的位置<xref:System.Windows.Forms.MenuStrip>。 您也可以移動個別的功能表項目之間的最上層功能表，或變更功能表中功能表項目的位置。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>若要將最上層的功能表和其功能表項目移至另一個最上層的位置  
  
1.  按一下並按住滑鼠左鍵，在您想要移動的功能表。  
  
2.  將插入點拖曳至預定新位置之前的最上層功能表，然後放開滑鼠左的按鈕。  
  
     選取的功能表會移到插入點的右邊。  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>若要將最上層的功能表和其功能表項目移至的下拉式清單位置  
  
1.  以滑鼠左鍵按一下您想要移動並按下 CTRL + X、 或功能表上按一下滑鼠右鍵，然後選取功能表**剪下**從捷徑功能表。  
  
2.  在目的地最上層功能表中，以滑鼠左鍵按一下預定新位置上方的功能表項目並按下 CTRL + V，或以滑鼠右鍵按一下預定新位置上方的功能表項目並選取**貼上**從捷徑功能表。  
  
     選取的功能表項目之後插入您剪下的功能表。  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>若要移動功能表項目內使用項目集合編輯器  
  
1.  以滑鼠右鍵按一下含有您想要移動的功能表項目的功能表。  
  
2.  從捷徑功能表，選擇 **編輯 DropDownItems**。  
  
3.  在**項目集合編輯器**，以滑鼠左鍵按一下您想要移動的功能表項目。  
  
4.  按一下向上和向下鍵移動功能表內功能表項目。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>若要移動使用鍵盤功能表中的功能表項目  
  
1.  按住 ALT 鍵。  
  
2.  按住滑鼠左鍵您想要移動的功能表項目。  
  
3.  將功能表項目拖曳至新的位置，然後放開滑鼠左的按鈕。  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>移至另一個功能表的功能表項目  
  
1.  以滑鼠左鍵按一下您想要移動並按下 CTRL + X，或以滑鼠右鍵按一下功能表項目並選擇 功能表項目**剪下**從捷徑功能表。  
  
2.  以滑鼠左鍵按一下將包含您剪下的功能表項目的功能表。  
  
3.  以滑鼠左鍵按一下預定新位置之前的功能表項目，然後按 CTRL + V，或以滑鼠右鍵按一下預定新位置，然後選取之前的功能表項目**貼上**從捷徑功能表。  
  
     選取的功能表項目之後插入您剪下的功能表項目。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
