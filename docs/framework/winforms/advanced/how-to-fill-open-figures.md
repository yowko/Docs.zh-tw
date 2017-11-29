---
title: "如何：填滿開放圖形"
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
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a8a2d5a13cac97063bf2a04969928c859a5954d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-fill-open-figures"></a>如何：填滿開放圖形
您可以藉由傳遞填滿路徑<xref:System.Drawing.Drawing2D.GraphicsPath>物件<xref:System.Drawing.Graphics.FillPath%2A>方法。 <xref:System.Drawing.Graphics.FillPath%2A>方法填入填滿模式 （替代或捲繞） 根據目前設定路徑的路徑。 如果路徑有任何開啟的數字，如同這些數字已關閉，已填入的路徑。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]關閉圖繪製直線其結束點從它的起點。  
  
## <a name="example"></a>範例  
 下列範例會建立一個開放的圖表 （弧形） 和一個封閉的圖形 （橢圓形） 的路徑。 <xref:System.Drawing.Graphics.FillPath%2A>方法中填入預設填滿模式，這是根據路徑<xref:System.Drawing.Drawing2D.FillMode.Alternate>。  
  
 下圖顯示的範例程式碼的輸出。 請注意，要填滿的路徑 (根據<xref:System.Drawing.Drawing2D.FillMode.Alternate>) 如同開放的圖表已關閉直線從其結束點至它的起點。  
  
 ![填入開啟路徑](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [GDI+ 中的圖形路徑](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
