---
title: HOW TO：Move ToolStripMenuItems
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
ms.openlocfilehash: 12554ee2225dbb186392b910ddfd7c2f69695e7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660212"
---
# <a name="how-to-move-toolstripmenuitems"></a>HOW TO：Move ToolStripMenuItems
在設計階段，您可以移動整個最上層的功能表與他們的功能表項目到不同位置<xref:System.Windows.Forms.MenuStrip>。 您也可以最上層的功能表間移動個別的功能表項目，或變更功能表中功能表項目的位置。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>若要將最上層的功能表和它的功能表項目移至另一個最上層的位置  
  
1.  按一下並按住滑鼠左鍵，在您想要移動的功能表上。  
  
2.  將插入點拖曳至想要的新位置之前的最上層功能表，然後放開滑鼠左的按鈕。  
  
     選取的功能表往右移動插入點。  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>若要將最上層的功能表和它的功能表項目移至 下拉式清單位置  
  
1.  以滑鼠左鍵按一下您想要移動並按下 CTRL + X，或以滑鼠右鍵按一下  功能表並選取  功能表**剪下**從捷徑功能表。  
  
2.  在目的地最上層功能表中，以滑鼠左鍵按一下預定新位置上方的功能表項目及按下 CTRL + V，或以滑鼠右鍵按一下預定新位置上方的功能表項目並選取**貼上**從捷徑功能表。  
  
     選取的功能表項目之後插入您剪下功能表。  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>若要移動的功能表項目集合編輯器的使用中的功能表項目  
  
1.  以滑鼠右鍵按一下含有您想要移動的功能表項目的功能表。  
  
2.  從捷徑功能表，選擇**編輯 DropDownItems**。  
  
3.  在 **項目集合編輯器**，以滑鼠左鍵按一下您想要移動的功能表項目。  
  
4.  按一下向上和向下鍵移動的功能表中功能表項目。  
  
5.  按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>若要移動使用鍵盤的功能表中功能表項目  
  
1.  按住 ALT 鍵。  
  
2.  按一下並按住滑鼠左鍵您想要移動的功能表項目。  
  
3.  將功能表項目拖曳至新的位置，然後放開滑鼠左的按鈕。  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>若要移至另一個功能表的功能表項目  
  
1.  以滑鼠左鍵按一下您想要移動並按下 CTRL + X，或以滑鼠右鍵按一下功能表項目，然後選擇功能表項目**剪下**從捷徑功能表。  
  
2.  以滑鼠左鍵按一下的功能表中會包含您剪下功能表項目。  
  
3.  以滑鼠左鍵按一下預定新位置之前的功能表項目及按下 CTRL + V，或以滑鼠右鍵按一下預定新位置，然後選取之前的功能表項目**貼上**從捷徑功能表。  
  
     選取的功能表項目之後插入您剪下功能表項目。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
