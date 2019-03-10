---
title: HOW TO：Windows Form 上繪製文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: ed7aa89c3bd3751ed93f5bda33a26a8309d39143
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703500"
---
# <a name="how-to-draw-text-on-a-windows-form"></a>HOW TO：Windows Form 上繪製文字
下列程式碼範例示範如何使用<xref:System.Drawing.Graphics.DrawString%2A>方法的<xref:System.Drawing.Graphics>表單上繪製文字。 或者，您可以使用<xref:System.Windows.Forms.TextRenderer>表單上繪製文字。 如需詳細資訊，請參閱[如何：使用 GDI 繪製文字](how-to-draw-text-with-gdi.md)。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 您不能呼叫<xref:System.Drawing.Graphics.DrawString%2A>方法中的<xref:System.Windows.Forms.Form.Load>事件處理常式。 如果調整大小或遮蔽另一種形式的表單時，將不會重新繪製的繪製的內容。 若要讓您自動重新繪製的內容，您應該覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   新細明體字型未安裝。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [圖形程式設計入門](getting-started-with-graphics-programming.md)
- [如何：使用 GDI 繪製文字](how-to-draw-text-with-gdi.md)
