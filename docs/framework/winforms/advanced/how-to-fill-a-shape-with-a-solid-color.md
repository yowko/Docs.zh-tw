---
title: "如何：使用純色填滿形狀"
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
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb3e160392a903083386d9942f8e2cfe31ee89a4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>如何：使用純色填滿形狀
若要利用純色填滿圖形時，建立<xref:System.Drawing.SolidBrush>物件，並再將其傳遞<xref:System.Drawing.SolidBrush>物件做為其中一個填滿方法的引數為<xref:System.Drawing.Graphics>類別。 下列範例會示範如何使用紅色的色彩填滿橢圓形。  
  
## <a name="example"></a>範例  
 下列程式碼，<xref:System.Drawing.SolidBrush.%23ctor%2A>建構函式接受<xref:System.Drawing.Color>物件做為其唯一的引數。 使用的值<xref:System.Drawing.Color.FromArgb%2A>方法來表示色彩的 alpha、 紅色、 綠色和藍色元件。 每個這些值必須是 0 到 255 範圍內。 第一個 255 表示的色彩就是完全不透明，而第二個 255 表示紅色元件的濃度。 兩個零表示綠色和藍色元件同時具有 0 的濃度。  
  
 四個數字 （0，0，100，60） 傳遞至<xref:System.Drawing.Graphics.FillEllipse%2A>方法指定的位置和大小的橢圓形之周框。 矩形的左上角 （0，0） 為 100，寬度和高度為 60。  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
