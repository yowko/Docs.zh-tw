---
title: HOW TO：使用設計工具隱藏 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 31c597a0e2cbf41484f19c8d4179823e9fb929ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941202"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>HOW TO：使用設計工具隱藏 ToolStripMenuItems
隱藏功能表項目是用來控制您的應用程式的使用者介面 (UI)，並限制使用者命令。 通常，您要隱藏整個功能表無法使用時，所有在其上的功能表項目。 這代表使用者分心。 此外，您可能想要隱藏和停用功能表或功能表項目，為單獨的隱藏不會防止使用者使用攠摝坫存取功能表命令。 如需有關如何停用功能表項目的詳細資訊，請參閱[How to:使用設計工具停用 ToolStripMenuItems](how-to-disable-toolstripmenuitems-using-the-designer.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>若要隱藏最上層的功能表和它的子功能表項目  
  
1. 選取最上層的功能表項目，並設定其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>或是<xref:System.Windows.Forms.ToolStripItem.Available%2A>屬性設`false`。  
  
     當您隱藏最上層的功能表項目時，同時也會隱藏該功能表內的所有功能表項目。 如果您按一下以外的地方上<xref:System.Windows.Forms.MenuStrip>設定之後<xref:System.Windows.Forms.ToolStripItem.Visible%2A>到`false`，整個最上層功能表項目和它的子功能表項目會消失從您的表單，因此顯示執行階段的影響您的動作。 若要在設計階段顯示隱藏的最上層功能表項目，請按一下<xref:System.Windows.Forms.MenuStrip>中**元件匣**，在**文件大綱**，或在屬性方格的頂端。  
  
> [!NOTE]
>  您很少會隱藏整個功能表除了中合併多個文件介面 (MDI) 子功能表。  
  
### <a name="to-hide-a-submenu-item"></a>若要隱藏的子功能表項目  
  
1. 選取子功能表項目，並設定其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性設`false`。  
  
     當您隱藏子功能表項目時，它仍會顯示在設計階段在表單上，讓您可以進一步的工作，輕鬆地選取它。 實際上會在執行階段隱藏。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
- [如何：使用設計工具停用 ToolStripMenuItems](how-to-disable-toolstripmenuitems-using-the-designer.md)
