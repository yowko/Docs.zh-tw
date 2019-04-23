---
title: HOW TO：將控制項新增至 ToolStripContentPanel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripContentPanel [Windows Forms], adding controls
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
ms.openlocfilehash: d228300e00a5c2be9cf530cd921865a01accab05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177875"
---
# <a name="how-to-add-a-control-to-a-toolstripcontentpanel"></a>HOW TO：將控制項新增至 ToolStripContentPanel
您可以程式設計方式將一個或多個控制項加入 <xref:System.Windows.Forms.ToolStripContentPanel>。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何將 <xref:System.Windows.Forms.RichTextBox> 加入 <xref:System.Windows.Forms.ToolStripContentPanel>。  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例需要：  
  
-   System、System.Data 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripContentPanel>
- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStripContainer 控制項](toolstripcontainer-control.md)
- [ToolStrip 控制項](toolstrip-control-windows-forms.md)
