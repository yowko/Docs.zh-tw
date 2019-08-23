---
title: HOW TO：使用設計工具隱藏 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 0e1cd7d1868adabd4d3eec9510f6ee567ba3867d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966622"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>作法：使用設計工具隱藏 ToolStripMenuItems
隱藏功能表項目是控制應用程式的使用者介面 (UI) 和限制使用者命令的一種方式。 當所有功能表項目都無法使用時, 通常會想要隱藏整個功能表。 這會為使用者提供較少的分散注意力。 此外, 您可能會想要隱藏和停用功能表或功能表項目, 因為單獨隱藏並不會防止使用者使用快速鍵來存取功能表命令。 如需停用功能表項目的詳細資訊[, 請參閱如何:使用設計](how-to-disable-toolstripmenuitems-using-the-designer.md)工具停用 ToolStripMenuItems。

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>隱藏最上層功能表及其子功能表專案

1. 選取最上層功能表項目, 並將其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>或<xref:System.Windows.Forms.ToolStripItem.Available%2A>屬性設定為`false`。

     當您隱藏最上層功能表項目時, 也會隱藏該功能表中的所有功能表項目。 如果您在 [設定<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ToolStripItem.Visible%2A>為`false`] 後按一下 [以外的位置], 整個最上層功能表項目和其子功能表專案就會從您的表單中消失, 因此會顯示動作的執行時間效果。 若要在設計階段顯示隱藏的最上層功能表項目, 請按一下<xref:System.Windows.Forms.MenuStrip> **元件**匣中的、[**檔大綱**] 或屬性方格頂端的。

> [!NOTE]
> 除了合併案例中的多重文件介面 (MDI) 子功能表以外, 您幾乎不會隱藏整個功能表。

## <a name="to-hide-a-submenu-item"></a>若要隱藏子功能表專案

1. 選取子功能表專案, 並將<xref:System.Windows.Forms.ToolStripItem.Visible%2A>其屬性`false`設定為。

     當您隱藏子功能表專案時, 它在設計階段仍會顯示在您的表單上, 讓您可以輕鬆地選取它以進行進一步的工作。 它實際上會在執行時間隱藏。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
- [如何：使用設計工具停用 ToolStripMenuItems](how-to-disable-toolstripmenuitems-using-the-designer.md)
