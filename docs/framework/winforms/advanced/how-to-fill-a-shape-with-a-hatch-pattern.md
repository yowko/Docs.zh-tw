---
title: 如何：以規劃圖樣填滿形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320059"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>如何：以規劃圖樣填滿形狀
影線圖樣是從兩個色彩組成：一個用於背景，另一個用於在背景上形成圖樣的線條。 若要以影線圖樣填滿封閉圖形，請使用 <xref:System.Drawing.Drawing2D.HatchBrush> 物件。 下列範例示範如何以影線圖樣填滿橢圓形：  
  
## <a name="example"></a>範例  
 @No__t_0 的函式會採用三個引數：影線樣式、影線線的色彩，以及背景的色彩。 影線樣式引數可以是來自 <xref:System.Drawing.Drawing2D.HatchStyle> 列舉的任何值。 @No__t_0 列舉中有超過50個元素;下列清單顯示其中幾個元素：  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 下圖顯示已填滿的橢圓形。  
  
  ![螢幕擷取畫面：以影線圖樣填滿的橢圓形看起來會像這樣。](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>請參閱

- [使用筆刷填滿形狀](using-a-brush-to-fill-shapes.md)
