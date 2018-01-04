---
title: "如何：繪製包含線條帽緣的線條"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
- drawing lines [Windows Forms], line caps
ms.assetid: eb68c3e1-c400-4886-8a04-76978a429cb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4048757e11724aa1e175d8b18c47f48d22d807e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-line-with-line-caps"></a>如何：繪製包含線條帽緣的線條
您可以繪製開頭或行尾的其中一種稱為線條頭尾圖案的數個圖形。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]支援數個線條頭尾圖案，例如循、 正方形、 菱形和箭頭。  
  
## <a name="example"></a>範例  
 您可以指定開始行 (開始 cap)，最後一行 （結束端點） 或虛線 (虛線 cap) 的虛線的線條端點。  
  
 下列範例會繪製直線箭頭一端與另一端的圓端點。 圖例中顯示產生的列：  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens4.gif "pens4")  
  
 [!code-csharp[System.Drawing.UsingAPen#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.UsingAPen#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   建立 Windows 表單，並處理表單的<xref:System.Windows.Forms.Control.Paint>事件。 將範例程式碼到<xref:System.Windows.Forms.Control.Paint>傳遞的事件處理常式`e`為<xref:System.Windows.Forms.PaintEventArgs>。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Drawing2D.LineCap?displayProperty=nameWithType>  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
