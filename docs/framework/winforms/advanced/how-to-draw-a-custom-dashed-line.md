---
title: HOW TO：繪製自訂短折線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 77b4b959523c6d35dece2d759eeb71be04b53d93
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538618"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>HOW TO：繪製自訂短折線
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供數個虛線樣式中所列<xref:System.Drawing.Drawing2D.DashStyle>列舉型別。 如果這些標準的虛線樣式不符合您的需求，您可以建立自訂虛線圖樣。  
  
## <a name="example"></a>範例  
 若要繪製自訂短折線，陣列中放入虛線和間距的長度和指派的值的陣列<xref:System.Drawing.Pen.DashPattern%2A>屬性<xref:System.Drawing.Pen>物件。 下列範例會繪製自訂短折線根據陣列`{5, 2, 15, 4}`。 如果您將陣列的項目乘以 5 的畫筆寬度時，您會收到`{25, 10, 75, 20}`。 顯示連字號替代的長度介於 25 和 75，之間和替代的長度介於 10 到 20 之間的空格。  
  
 下圖顯示產生的虛線。 請注意，最終的 dash 必須是少於 25 個單位，以便在列可以在結束 （405，5）。  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。 貼上上述程式碼到<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱
- [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
