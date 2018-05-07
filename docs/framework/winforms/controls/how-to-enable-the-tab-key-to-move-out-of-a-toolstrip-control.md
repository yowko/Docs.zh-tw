---
title: 如何：啟用 TAB 鍵來移至 ToolStrip 控制項之外
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: 0af6c4c308ac1988b5f1babd80897afd5bf6a4d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>如何：啟用 TAB 鍵來移至 ToolStrip 控制項之外
使用下列程序可讓使用者按下 TAB 鍵以移出<xref:System.Windows.Forms.ToolStrip>定位順序中的下一個控制項。  
  
 <xref:System.Windows.Forms.ToolStrip>接受第一次按下 TAB 鍵，和箭號索引鍵選取項目內<xref:System.Windows.Forms.ToolStrip>。 當使用者在第二次按下 TAB 鍵時，它將使用者帶至下一個控制項定位順序中。  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>若要讓使用者按下 TAB 鍵，從 ToolStrip 移動到下一個控制項  
  
-   設定<xref:System.Windows.Forms.ToolStrip.TabStop%2A>屬性<xref:System.Windows.Forms.ToolStrip>至`true`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
