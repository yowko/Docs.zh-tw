---
title: 如何：在 Windows Form 上繪製文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: 9369a4ed26107bdc395d455ba6fb8420fd895d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-text-on-a-windows-form"></a>如何：在 Windows Form 上繪製文字
下列程式碼範例示範如何使用<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>表單上繪製文字。 或者，您可以使用<xref:System.Windows.Forms.TextRenderer>的表單上繪製文字。 如需詳細資訊，請參閱[How to： 使用 GDI 繪製的文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 您不能呼叫<xref:System.Drawing.Graphics.DrawString%2A>方法中的<xref:System.Windows.Forms.Form.Load>事件處理常式。 如果調整大小或遮蔽另一種形式的形式，將不會重新繪製內容。 若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   新細明體字型未安裝。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Windows.Forms.TextRenderer.DrawText%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [圖形程式設計入門](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [操作說明：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
