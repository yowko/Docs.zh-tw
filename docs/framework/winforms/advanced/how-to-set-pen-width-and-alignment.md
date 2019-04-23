---
title: HOW TO：設定畫筆寬度和對齊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: bc2ac2587554215ef3b2c2580413fbbb894aa687
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074972"
---
# <a name="how-to-set-pen-width-and-alignment"></a>HOW TO：設定畫筆寬度和對齊
當您建立<xref:System.Drawing.Pen>，您可以提供畫筆寬度作為建構函式的引數之一。 您也可以變更畫筆寬度<xref:System.Drawing.Pen.Width%2A>屬性<xref:System.Drawing.Pen>類別。  
  
 假設線條的寬度為 0。 當您繪製一條線是 1 個像素寬時，像素會在假設線條上置中對齊。 如果您繪製多個像素寬的線條，像素為單位可能是在假設線條上置中或出現在假設線的一端。 您可以設定的畫筆對齊屬性<xref:System.Drawing.Pen>來判斷如何使用該畫筆繪製的像素會放置相對於理論的行。  
  
 值<xref:System.Drawing.Drawing2D.PenAlignment.Center>， <xref:System.Drawing.Drawing2D.PenAlignment.Outset>，並<xref:System.Drawing.Drawing2D.PenAlignment.Inset>出現在下列程式碼範例屬於<xref:System.Drawing.Drawing2D.PenAlignment>列舉型別。  
  
 下列程式碼範例會繪製一條線兩次： 一次使用黑色畫筆的寬度為 1，另一次以綠色畫筆的寬度為 10。  
  
### <a name="to-vary-the-width-of-a-pen"></a>變更畫筆的寬度  
  
-   設定的值<xref:System.Drawing.Pen.Alignment%2A>屬性設<xref:System.Drawing.Drawing2D.PenAlignment.Center>（預設值），指定將在假設線條上置中以綠色的畫筆繪製的像素為單位。 下圖顯示產生的列。  
  
     ![以綠色反白顯示黑色細線。](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-line.gif)  
  
     下列程式碼範例會繪製矩形兩次： 一次使用黑色畫筆的寬度為 1，另一次以綠色畫筆的寬度為 10。  
  
     [!code-csharp[System.Drawing.UsingAPen#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>若要變更畫筆的對齊方式  
  
-   設定的值<xref:System.Drawing.Pen.Alignment%2A>屬性設<xref:System.Drawing.Drawing2D.PenAlignment.Center>來指定將在矩形的界限上置中以綠色的畫筆繪製的像素。  
  
     下圖顯示產生的矩形：
  
     ![以綠色反白顯示與黑色細線繪製矩形。](./media/how-to-set-pen-width-and-alignment/green-pixels-centered-rectangle.gif)  
  
     [!code-csharp[System.Drawing.UsingAPen#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>若要建立插頁畫筆  
  
-   變更綠色手寫筆的對齊方式，藉由修改上述的程式碼範例中的第三個陳述式，如下所示：  
  
     [!code-csharp[System.Drawing.UsingAPen#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     現在的像素寬的綠色列中會出現在矩形內部如下圖所示：
  
     ![以黑線與寬綠線內繪製一個矩形。](./media/how-to-set-pen-width-and-alignment/green-pixels-inside-rectangle.gif)  
  
## <a name="see-also"></a>另請參閱

- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
