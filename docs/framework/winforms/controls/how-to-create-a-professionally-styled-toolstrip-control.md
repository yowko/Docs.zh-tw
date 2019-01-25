---
title: HOW TO：建立專業樣式的 ToolStrip 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 1e6455ebabfa5b27301f98b89861348b28d415af
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690198"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>HOW TO：建立專業樣式的 ToolStrip 控制項
您可以藉由自行撰寫衍生自 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 類型的類別，賦與應用程式的 <xref:System.Windows.Forms.ToolStrip> 控制項專業外觀和行為 (外觀及操作)。  
  
 沒有這項功能在 Visual Studio 中的廣泛支援。  
  
 請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用<xref:System.Windows.Forms.ToolStrip>控制項，以建立複合控制項，以模擬**瀏覽窗格**Microsoft® Outlook® 提供的。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  另請參閱[逐步解說：建立專業樣式的 ToolStrip 控制項](walkthrough-creating-a-professionally-styled-toolstrip-control.md)。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
- [如何：對表單提供標準功能表項目](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
