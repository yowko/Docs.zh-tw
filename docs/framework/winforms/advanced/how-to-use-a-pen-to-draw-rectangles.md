---
title: "如何：使用畫筆繪製矩形"
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
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7257fa21432ec5d849a257f4a5e412515f474363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>如何：使用畫筆繪製矩形
若要繪製的矩形，您需要<xref:System.Drawing.Graphics>物件和<xref:System.Drawing.Pen>物件。 <xref:System.Drawing.Graphics>物件提供<xref:System.Drawing.Graphics.DrawRectangle%2A>方法，而<xref:System.Drawing.Pen>物件儲存的行，例如色彩和寬度的功能。  
  
## <a name="example"></a>範例  
 下列範例會繪製在其左上角的矩形 （10，10）。 矩形的寬度為 100，高度為 50。 第二個引數傳遞給<xref:System.Drawing.Pen.%23ctor%2A>建構函式表示畫筆寬度為 5 像素。  
  
 繪製矩形，畫筆內置矩形的界限上。 矩形的側邊的畫筆寬度為 5，因為會繪製 5 像素寬、 這類繪製 1 個像素界限，2 個像素繪製在內部和外部繪製 2 像素為單位。 如需有關畫筆對齊的詳細資訊，請參閱[How to： 設定畫筆寬度和對齊](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)。  
  
 下圖顯示產生的矩形。 虛線顯示，其中會有已繪製矩形如果畫筆寬度便是一個像素。 矩形左上角的放大的檢視顯示黑色粗線會置於虛線。  
  
 ![畫筆](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>請參閱  
 [使用畫筆繪製線條和形狀](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
