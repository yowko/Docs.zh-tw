---
title: HOW TO：複製 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
ms.openlocfilehash: c59af175a6ee23395e19247efd8fa15e6d19ae66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746935"
---
# <a name="how-to-copy-toolstripmenuitems"></a>HOW TO：複製 ToolStripMenuItems
在設計階段，您可以將整個最上層功能表及其子功能表項目複製到 <xref:System.Windows.Forms.MenuStrip>上的不同位置。 您也可以在最上層功能表之間複製個別功能表項目，或變更功能表內功能表項目的位置。  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a>將最上層功能表及其子功能表項目複製到另一個最上層位置  
  
1. 以滑鼠左鍵按一下您要複製的功能表，然後按 CTRL+C，或以滑鼠右鍵按一下功能表，然後從捷徑功能表選取 [複製]  。  
  
2. 以滑鼠左鍵按一下預定新位置之後的最上層功能表，然後按 CTRL+V，或以滑鼠右鍵按一下預定新位置之前的最上層功能表項目，然後從捷徑功能表選取 [貼上]  。  
  
     您所複製的功能表會在選取的最上層功能表之前插入。  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a>將最上層功能表及其子功能表項目複製到下拉式清單位置  
  
1. 以滑鼠左鍵按一下您要移動的功能表，然後按 CTRL+C，或以滑鼠右鍵按一下功能表，然後從捷徑功能表選取 [複製]  。  
  
2. 在目的地最上層功能表中，以滑鼠左鍵按一下預定新位置上方的的子功能表項目，然後按 CTRL+V，或以滑鼠右鍵按一下預定新位置上方的的子功能表項目，然後從捷徑功能表選取 [貼上]  。  
  
     您所複製的功能表會在選取的子功能表項目之前插入。  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a>將子功能表項目複製到另一個功能表  
  
1. 以滑鼠左鍵按一下您要複製的子功能表項目，然後按 CTRL+C，或以滑鼠右鍵按一下子功能表項目，然後從捷徑功能表選擇 [複製]  。  
  
2. 以滑鼠左鍵按一下包含您剪下之子功能表項目的功能表。  
  
3. 以滑鼠左鍵按一下預定新位置之前的子功能表項目，然後按 CTRL+V，或以滑鼠右鍵按一下預定新位置之前的子功能表項目，然後從捷徑功能表選取 [貼上]  。  
  
     您所複製的子功能表項目會在選取的子功能表項目之前插入。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
