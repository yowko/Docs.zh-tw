---
title: 作法：移動 ToolStripMenuItems
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
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039802"
---
# <a name="how-to-move-toolstripmenuitems"></a>作法：移動 ToolStripMenuItems
在設計階段, 您可以將整個最上層功能表及其功能表項目移至上<xref:System.Windows.Forms.MenuStrip>的不同位置。 您也可以在最上層功能表之間移動個別的功能表項目, 或變更功能表中功能表項目的位置。

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>將最上層功能表及其功能表項目移至另一個最上層位置

1. 在您要移動的功能表上, 按一下並按住滑鼠左鍵。

2. 將插入點拖曳至所需新位置之前的最上層功能表, 然後放開滑鼠左鍵。

     選取的功能表會移至插入點的右邊。

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>將最上層功能表及其功能表項目移至下拉式位置

1. 以滑鼠左鍵按一下您想要移動的功能表, 然後按 CTRL + X, 或以滑鼠右鍵按一下功能表, 然後從快捷方式功能表選取 [**剪**下]。

2. 在目的地最上層功能表中, 以滑鼠左鍵按一下預定新位置上方的功能表項目, 然後按 CTRL + V, 或以滑鼠右鍵按一下預定新位置上方的功能表項目, 然後從快捷方式功能表選取 [**貼**上]。

     您剪下的功能表會在選取的功能表項目之後插入。

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>使用 Items 集合編輯器移動功能表中的功能表項目

1. 以滑鼠右鍵按一下包含您要移動之功能表項目的功能表。

2. 從快捷方式功能表中, 選擇 [**編輯控制項 dropdownitems**]。

3. 在 [**專案集合編輯器**] 中, 以滑鼠左鍵按一下您要移動的功能表項目。

4. 按一下向上箭號和向下鍵, 即可移動功能表中的功能表項目。

5. 按一下 [確定]。

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>使用鍵盤移動功能表中的功能表項目

1. 按住 ALT 鍵。

2. 在您要移動的功能表項目上, 按一下並按住滑鼠左鍵。

3. 將功能表項目拖曳至新位置, 然後放開滑鼠左鍵。

## <a name="to-move-a-menu-item-to-another-menu"></a>將功能表項目移至另一個功能表

1. 以滑鼠左鍵按一下您想要移動的功能表項目, 然後按 CTRL + X, 或以滑鼠右鍵按一下功能表項目, 然後從快捷方式功能表選擇 [**剪**下]。

2. 以滑鼠左鍵按一下將包含您剪下之功能表項目的功能表。

3. 以滑鼠左鍵按一下預定新位置之前的功能表項目, 然後按 CTRL + V, 或以滑鼠右鍵按一下預定新位置之前的功能表項目, 然後從快捷方式功能表選取 [**貼**上]。

     您剪下的功能表項目會插入選取的功能表項目之後。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
