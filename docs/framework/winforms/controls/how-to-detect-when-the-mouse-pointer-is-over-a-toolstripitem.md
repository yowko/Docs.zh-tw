---
title: "如何：當滑鼠指標移至 ToolStripItem 上時偵測"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 633b92bf6da837b3727001c621548fa58b230102
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>如何：當滑鼠指標移至 ToolStripItem 上時偵測
使用下列程序來偵測當滑鼠指標位於<xref:System.Windows.Forms.ToolStripItem>。  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>當指標移至 toolstripitem 上時偵測  
  
-   使用<xref:System.Windows.Forms.ToolStripItem.Selected%2A>中的項目屬性<xref:System.Windows.Forms.ToolStripItem.CanSelect%2A>是`true`。  
  
     這會讓您不需要同步處理<xref:System.Windows.Forms.ToolStripItem.MouseEnter>和<xref:System.Windows.Forms.ToolStripItem.MouseLeave>事件。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
