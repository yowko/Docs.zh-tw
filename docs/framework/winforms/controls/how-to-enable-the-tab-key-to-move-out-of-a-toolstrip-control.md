---
title: HOW TO：啟用 TAB 鍵移至 ToolStrip 控制項之外
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
ms.openlocfilehash: a98c8a54389daa898c877a08f8cc2cae46a11da9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663061"
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>HOW TO：啟用 TAB 鍵移至 ToolStrip 控制項之外
使用下列程序以啟用使用者按下 TAB 鍵來移出<xref:System.Windows.Forms.ToolStrip>定位順序中的下一個控制項。  
  
 <xref:System.Windows.Forms.ToolStrip>接受第一次按下 TAB 鍵和箭號索引鍵選取項目內<xref:System.Windows.Forms.ToolStrip>。 當使用者按下 TAB 鍵一次時，它將使用者帶到下一個控制項定位順序中。  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>若要啟用使用者按下 TAB 鍵來移出 ToolStrip 以的下一個控制項  
  
-   設定<xref:System.Windows.Forms.ToolStrip.TabStop%2A>的屬性<xref:System.Windows.Forms.ToolStrip>至`true`。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.TabStop%2A>
- [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
