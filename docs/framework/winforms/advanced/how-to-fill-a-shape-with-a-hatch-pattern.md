---
title: HOW TO：填滿形狀以規劃圖樣
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: 885f0d22e83767bda3ef76c54f0857dd2a148344
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719711"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>HOW TO：填滿形狀以規劃圖樣
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
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱
- [使用筆刷填滿形狀](using-a-brush-to-fill-shapes.md)
