---
title: 作法：使用設計工具停用 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: fd80a6543c83ae957cd9c51b068d0702559f0925
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040262"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>作法：使用設計工具停用 ToolStripMenuItems
您可以啟用和停用功能表項目以回應使用者活動, 以限制或放寬使用者可能進行的命令。 建立功能表項目時, 預設會啟用這些專案, 但可透過<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性來調整。 您可以在設計階段于 [**屬性**] 視窗中操作這個屬性, 或是在程式碼中設定它以程式設計方式。 如需詳細資訊，請參閱[如何：停用](how-to-disable-toolstripmenuitems.md)ToolStripMenuItems。

## <a name="to-disable-a-menu-item-at-design-time"></a>若要在設計階段停用功能表項目

1. 在表單上選取功能表項目時, 將<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性設定為。 `false`

    > [!TIP]
    >  停用功能表中的第一個或最上層功能表項目, 會停用功能表中包含的所有功能表項目。 同樣地, 停用具有子功能表專案的功能表項目會停用子功能表專案。 如果指定功能表上的所有命令都無法供使用者使用, 就會被視為良好的程式設計實務, 可以隱藏和停用整個功能表, 因為這會呈現全新的使用者介面。 您應該隱藏和停用功能表, 因為單獨隱藏並不會阻止透過快速鍵存取功能表命令。 將最上層功能表項目的`false` 屬性設定為,以隱藏整個功能表。<xref:System.Windows.Forms.ToolStripItem.Visible%2A>

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [如何：隱藏 ToolStripMenuItems](how-to-hide-toolstripmenuitems.md)
- [MenuStrip 控制項概觀](menustrip-control-overview-windows-forms.md)
