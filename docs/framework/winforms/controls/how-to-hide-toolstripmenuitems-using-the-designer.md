---
title: "如何：使用設計工具隱藏 ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06a95581e156a7027c8fa0bda6e5fbc4babdb85b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>如何：使用設計工具隱藏 ToolStripMenuItems
隱藏功能表項目是能夠控制您的應用程式的使用者介面 (UI)，並限制使用者命令。 通常，您要隱藏整個功能表，當所有在其上的功能表項目都無法使用。 這代表使用者的分心。 此外，您可能想要隱藏並停用功能表或功能表項目，如單獨隱藏不會阻止使用者使用快速鍵來存取功能表命令。 如需有關如何停用功能表項目的詳細資訊，請參閱[如何： 停用 ToolStripMenuItems 使用設計工具](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>若要隱藏最上層功能表及其子功能表項目  
  
1.  選取最上層功能表項目，並設定其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>或<xref:System.Windows.Forms.ToolStripItem.Available%2A>屬性`false`。  
  
     當您隱藏最上層功能表項目時，也會隱藏該功能表中的所有功能表項目。 如果您按一下以外的地方上<xref:System.Windows.Forms.MenuStrip>之後設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>至`false`，整個最上層功能表項目和它的子功能表項目會從您的表單，因此顯示您的動作的執行階段影響消失。 若要在設計階段顯示隱藏的最上層功能表項目，請按一下<xref:System.Windows.Forms.MenuStrip>中**元件匣**，請在**文件大綱**，或在屬性方格的頂端。  
  
> [!NOTE]
>  您很少會隱藏整個功能表除了中合併多個文件介面 (MDI) 子功能表。  
  
### <a name="to-hide-a-submenu-item"></a>若要隱藏子功能表項目  
  
1.  選取的子功能表項目，並設定其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性`false`。  
  
     當您隱藏子功能表項目時，它仍會顯示在設計階段在表單上，因此您可以進一步的工作，輕鬆地選取它。 實際上會在執行階段隱藏。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [MenuStrip 控制項概觀](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [操作說明：使用設計工具停用 ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
