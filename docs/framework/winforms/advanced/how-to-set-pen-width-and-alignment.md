---
title: 如何：設定畫筆寬度和對齊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pens [Windows Forms], setting width
- pens [Windows Forms], setting alignment
ms.assetid: a202af36-4d31-4401-a126-b232f51db581
ms.openlocfilehash: 8ac125978405f39cd26680338cdabb661ad92d16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522278"
---
# <a name="how-to-set-pen-width-and-alignment"></a>如何：設定畫筆寬度和對齊
當您建立<xref:System.Drawing.Pen>，您可以做為其中一個建構函式的引數提供的畫筆寬度。 您也可以變更畫筆寬度<xref:System.Drawing.Pen.Width%2A>屬性<xref:System.Drawing.Pen>類別。  
  
 理論上的線條的寬度為 0。 當您繪製一條線來 1 個像素寬時，像素會置於理論的線條。 如果您繪製一條線來為多個像素寬，像素為單位是置於理論的線條，或顯示理論上一行的另一端。 您可以設定的畫筆對齊屬性<xref:System.Drawing.Pen>來決定如何將使用該畫筆繪製的像素放置相對於理論的行。  
  
 值<xref:System.Drawing.Drawing2D.PenAlignment.Center>， <xref:System.Drawing.Drawing2D.PenAlignment.Outset>，和<xref:System.Drawing.Drawing2D.PenAlignment.Inset>會出現在下列程式碼範例屬於<xref:System.Drawing.Drawing2D.PenAlignment>列舉型別。  
  
 下列程式碼範例會繪製一條線兩次： 一次使用黑色畫筆寬度為 1，另一次使用的綠色的畫筆寬度為 10。  
  
### <a name="to-vary-the-width-of-a-pen"></a>若要改變的畫筆寬度  
  
-   值設定<xref:System.Drawing.Pen.Alignment%2A>屬性<xref:System.Drawing.Drawing2D.PenAlignment.Center>（預設值） 來指定將在該行理論上置中以綠色的畫筆繪製的像素為單位。 下圖顯示產生的線條。  
  
     ![畫筆](../../../../docs/framework/winforms/advanced/media/pens1a.gif "pens1A")  
  
     下列程式碼範例會繪製矩形兩次： 一次使用黑色畫筆寬度為 1，另一次使用的綠色的畫筆寬度為 10。  
  
     [!code-csharp[System.Drawing.UsingAPen#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#41)]
     [!code-vb[System.Drawing.UsingAPen#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#41)]  
  
### <a name="to-change-the-alignment-of-a-pen"></a>若要變更畫筆對齊  
  
-   值設定<xref:System.Drawing.Pen.Alignment%2A>屬性<xref:System.Drawing.Drawing2D.PenAlignment.Center>來指定將在矩形的界限上置中以綠色的畫筆繪製的像素。  
  
     下圖顯示產生的矩形。  
  
     ![畫筆](../../../../docs/framework/winforms/advanced/media/pens2.gif "pens2")  
  
     [!code-csharp[System.Drawing.UsingAPen#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#42)]
     [!code-vb[System.Drawing.UsingAPen#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#42)]  
  
### <a name="to-create-an-inset-pen"></a>若要建立內凹畫筆  
  
-   變更綠色畫筆的對齊方式，藉由修改上述的程式碼範例中的第三個陳述式，如下所示：  
  
     [!code-csharp[System.Drawing.UsingAPen#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#43)]
     [!code-vb[System.Drawing.UsingAPen#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#43)]  
  
     現在的像素寬的綠色列中會出現在矩形內部下圖所示。  
  
     ![畫筆](../../../../docs/framework/winforms/advanced/media/pens3.gif "pens3")  
  
## <a name="see-also"></a>另請參閱  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
