---
title: HOW TO：使用影線圖樣填滿形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: f5399c4151b335090f4b93be041375b8c2781afa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118114"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>HOW TO：使用影線圖樣填滿形狀
從兩個色彩來進行以規劃圖樣： 一個用於背景，一個在背景上形成模式的程式碼行。 若要以規劃圖樣填滿一個封閉的形狀，請使用<xref:System.Drawing.Drawing2D.HatchBrush>物件。 下列範例示範如何使用以規劃圖樣填滿橢圓形：  
  
## <a name="example"></a>範例  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A>建構函式接受三個引數： 影線樣式、 規劃線條、 色彩和背景的色彩。 影線樣式引數可以是任何值<xref:System.Drawing.Drawing2D.HatchStyle>列舉型別。 有 50 位以上的項目中<xref:System.Drawing.Drawing2D.HatchStyle>列舉型別，其中幾個項目會顯示下面清單中：  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 下圖顯示實心的橢圓形。  
  
 ![影線圖樣](./media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [使用筆刷填滿形狀](using-a-brush-to-fill-shapes.md)
