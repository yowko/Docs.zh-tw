---
title: "如何：以規劃圖樣填滿形狀"
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
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36ee5b7152dabc7dcd1e0c844e8549eb03aa0045
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>如何：以規劃圖樣填滿形狀
從兩個色彩來進行規劃圖樣： 一個用於背景，一個背景上形成圖樣的程式碼行。 若要規劃圖樣填滿封閉的圖形，請使用<xref:System.Drawing.Drawing2D.HatchBrush>物件。 下列範例會示範如何以規劃圖樣填滿橢圓形：  
  
## <a name="example"></a>範例  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A>建構函式接受三個引數： 影線樣式、 影線線條的色彩和背景的色彩。 影線樣式引數可以是任何值<xref:System.Drawing.Drawing2D.HatchStyle>列舉型別。 有多個五十個中的項目<xref:System.Drawing.Drawing2D.HatchStyle>列舉，其中幾個項目會顯示下面清單中：  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 下圖顯示實心的橢圓形。  
  
 ![影線圖樣](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
