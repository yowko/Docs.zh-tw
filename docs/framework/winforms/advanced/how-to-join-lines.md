---
title: HOW TO：聯結線條
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: 445d7f12f57137c6b06a074eeaf0574eb027a723
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723285"
---
# <a name="how-to-join-lines"></a>HOW TO：聯結線條
線條聯結是指的常見區域由其結束符合或重疊的兩行所構成。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供三個線條聯結樣式： 儀表、 斜面，和捨入。 線條聯結樣式是屬性<xref:System.Drawing.Pen>類別。 當您指定的線條聯結樣式<xref:System.Drawing.Pen>物件，將會聯結樣式套用到所有連接的直線，任何<xref:System.Drawing.Drawing2D.GraphicsPath>使用該畫筆繪製的物件。  
  
 下圖顯示斜面的線條聯結範例的結果。  
  
 ![顯示圖例，線條的聯結。](./media/how-to-join-lines/joined-beveled-lines.gif)  
  
## <a name="example"></a>範例  
 您可以使用來指定線條聯結樣式<xref:System.Drawing.Pen.LineJoin%2A>屬性<xref:System.Drawing.Pen>類別。 此範例示範斜切的線之間的聯結的水平線和垂直線。 下列程式碼的值<xref:System.Drawing.Drawing2D.LineJoin.Bevel>指派給<xref:System.Drawing.Pen.LineJoin%2A>屬性是成員的<xref:System.Drawing.Drawing2D.LineJoin>列舉型別。 其他成員<xref:System.Drawing.Drawing2D.LineJoin>列舉型別都<xref:System.Drawing.Drawing2D.LineJoin.Miter>和<xref:System.Drawing.Drawing2D.LineJoin.Round>。  
  
 [!code-csharp[System.Drawing.UsingAPen#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
