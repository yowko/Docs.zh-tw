---
title: 如何：使用設計工具停用 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: f97c622719c0f76fe8ce7ea34b9324110508b6e9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486590"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>如何：使用設計工具停用 ToolStripMenuItems
您可以限制，或擴大使用者可能會進行啟用和停用功能表項目，以回應使用者活動的命令。 依預設會啟用功能表項目，當建立，但這可以透過調整<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性。 您可以使用這個屬性在設計階段**屬性**視窗或以程式設計方式在程式碼中設定它。 如需詳細資訊，請參閱 <<c0> [ 如何： 停用 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>若要在設計階段停用功能表項目  
  
1.  選取表單上的功能表項目，設定<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>屬性設`false`。  
  
    > [!TIP]
    >  停用功能表中的第一個或最上層功能表項目，就會停用功能表內包含的所有功能表項目。 同樣地，停用功能表項目具有子功能表項目停用的子功能表項目。 如果使用者無法使用指定的功能表上的所有命令，它會視為良好的程式設計作法，同時隱藏並停用整個功能表中，這帶來全新的使用者介面。 您應該同時隱藏並停用 [] 功能表中，因為單獨隱藏不會防止存取功能表命令，透過攠摝坫。 設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性的最上層的功能表項目`false`隱藏整個功能表。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [操作說明：隱藏 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
