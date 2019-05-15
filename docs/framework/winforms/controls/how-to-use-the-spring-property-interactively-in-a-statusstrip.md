---
title: HOW TO：在 StatusStrip 中以互動方式使用 Spring 屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: 8750c48d08161260a1dba6ab69098980f25a5d55
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589642"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>HOW TO：在 StatusStrip 中以互動方式使用 Spring 屬性
您可以使用 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性，將 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項放置在 <xref:System.Windows.Forms.StatusStrip> 控制項中。 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性會判斷 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項是否會自動填滿 <xref:System.Windows.Forms.StatusStrip> 控制項上的可用空間。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性，將 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項放置在 <xref:System.Windows.Forms.StatusStrip> 控制項中。 <xref:System.Windows.Forms.ToolStripItem.Click> 事件處理常式會執行 Exclusive-OR (XOR) 運算，以切換 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> 屬性的值。  
  
 若要使用此程式碼範例，編譯並執行應用程式，然後按**Middle (Spring)** 上<xref:System.Windows.Forms.StatusStrip>控制項的值切換為<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>屬性。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System.Design、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [ToolStrip 控制項](toolstrip-control-windows-forms.md)
