---
title: HOW TO：繪製包含線條帽緣的線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
ms.openlocfilehash: 05c678b25563eb7a4e2e5ce0e49138b5445b4764
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707595"
---
# <a name="how-to-draw-a-line-with-line-caps"></a>HOW TO：繪製包含線條帽緣的線條
您可以在其中一種稱為線條帽緣的數個圖形中繪製的開頭或行結尾。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 支援數個線條端點，例如循、 正方形、 菱形、 和箭頭。  
  
## <a name="example"></a>範例  
 您可以指定開始的行 （開始端點），最後一行 （結束端點） 或以虛線 (dash cap) 的連字號的線條端點。  
  
 下列範例會繪製含有某一端點上的箭頭和圓形的帽緣，另一端的線條。 圖例中顯示產生的列：  
  
 ![畫筆](./media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。 範例程式碼到貼<xref:System.Windows.Forms.Control.Paint>傳遞的事件處理常式`e`做為<xref:System.Windows.Forms.PaintEventArgs>。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
