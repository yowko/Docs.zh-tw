---
title: HOW TO：當滑鼠指標 Toolstripitem 上時偵測
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 39173490c31711cca9f26f5f0cb2ab493546dda3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720805"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>HOW TO：當滑鼠指標 Toolstripitem 上時偵測
使用下列程序來偵測當滑鼠指標移<xref:System.Windows.Forms.ToolStripItem>。  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>偵測當滑鼠指標 toolstripitem 上時  
  
-   使用<xref:System.Windows.Forms.ToolStripItem.Selected%2A>屬性中的項目<xref:System.Windows.Forms.ToolStripItem.CanSelect%2A>是`true`。  
  
     這會讓您不需要同步處理<xref:System.Windows.Forms.ToolStripItem.MouseEnter>和<xref:System.Windows.Forms.ToolStripItem.MouseLeave>事件。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
