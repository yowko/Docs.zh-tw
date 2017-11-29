---
title: "如何： 繪製一連串的 B &#233; zier 曲線"
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
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76a0ab96f40c1b8d9db6f61d19ece82066b63eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>如何： 繪製一連串的 B &#233; zier 曲線
您可以使用<xref:System.Drawing.Graphics.DrawBeziers%2A>方法<xref:System.Drawing.Graphics>類別繪製一系列連接的貝茲曲線。  
  
## <a name="example"></a>範例  
 下列範例會繪製包含兩個連接的貝茲曲線的曲線。 第一個貝茲曲線的結束點是第二個貝茲曲線開始點。  
  
 下圖顯示連接的曲線，和七個點。  
  
 ![貝茲曲線](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [GDI+ 中的貝茲曲線](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
