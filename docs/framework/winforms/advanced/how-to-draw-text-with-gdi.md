---
title: 作法：使用 GDI 繪製文字
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956547"
---
# <a name="how-to-draw-text-with-gdi"></a>作法：使用 GDI 繪製文字
透過<xref:System.Windows.Forms.TextRenderer.DrawText%2A> 類別<xref:System.Windows.Forms.TextRenderer>中的方法, 您可以存取 GDI 功能, 以在表單或控制項上繪製文字。 GDI 文字轉譯通常提供比 GDI + 更佳的效能和更精確的文字測量。  
  
> [!NOTE]
> 列印時不支援<xref:System.Windows.Forms.TextRenderer>類別的方法。<xref:System.Windows.Forms.TextRenderer.DrawText%2A> 列印時, 請一律使用<xref:System.Drawing.Graphics.DrawString%2A> <xref:System.Drawing.Graphics>類別的方法。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法, 在矩形內的多行上繪製文字。  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 若要使用<xref:System.Windows.Forms.TextRenderer>類別轉譯文字, 您<xref:System.Drawing.IDeviceContext>需要, 例如<xref:System.Drawing.Graphics>和 a <xref:System.Drawing.Font>、繪製文字的位置, 以及應該繪製的色彩。 (選擇性) 您可以使用<xref:System.Windows.Forms.TextFormatFlags>列舉來指定文字格式。  
  
 如需取得的<xref:System.Drawing.Graphics>詳細資訊, 請參閱[如何:建立繪圖](how-to-create-graphics-objects-for-drawing.md)的繪圖物件。 如需有關如何建立的<xref:System.Drawing.Font>詳細資訊[, 請參閱如何:結構字型家族和](how-to-construct-font-families-and-fonts.md)字型。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述程式碼範例的設計目的是要與 Windows Forms 搭配使用, 而且<xref:System.Windows.Forms.PaintEventArgs>它需要`e`, <xref:System.Windows.Forms.PaintEventHandler>這是的參數。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [使用字型和文字](using-fonts-and-text.md)
