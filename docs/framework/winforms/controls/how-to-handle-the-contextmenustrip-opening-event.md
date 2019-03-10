---
title: HOW TO：處理 ContextMenuStrip Opening 事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
ms.openlocfilehash: 179411da96362fd9ba42e2b97682f335beb894c1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715447"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>HOW TO：處理 ContextMenuStrip Opening 事件
您可以自訂的行為您<xref:System.Windows.Forms.ContextMenuStrip>藉由處理控制項<xref:System.Windows.Forms.ToolStripDropDown.Opening>事件。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何處理<xref:System.Windows.Forms.ToolStripDropDown.Opening>事件。 事件處理常式中將項目以動態方式加入<xref:System.Windows.Forms.ContextMenuStrip>控制項。 完整的程式碼範例，請參閱[How to:以動態方式新增 ToolStrip 項目](how-to-add-toolstrip-items-dynamically.md)。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 設定<xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType>屬性設`true`以防止開啟的功能表。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [ToolStrip 控制項](toolstrip-control-windows-forms.md)
