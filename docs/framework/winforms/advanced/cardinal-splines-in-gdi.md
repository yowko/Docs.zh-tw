---
title: "GDI+ 中的基本曲線"
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
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ad417ee61026f6573f19e70409511e0b28e4d78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cardinal-splines-in-gdi"></a>GDI+ 中的基本曲線
基本曲線是一連串個別聯結成更大的曲線的曲線。 曲線的點和張力參數陣列所指定。 基本曲線平滑通過陣列; 中的每個點有沒有尖角和曲線的 tightness 沒有突然變更。 下圖顯示一組點和通過集中的每個點的基本曲線。  
  
 ![基本曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>實體和數學曲線  
 實體的曲線是指薄木材或其他彈性的資料。 之前的數學曲線，設計工具會用來繪製曲線實體曲線。 設計工具會對於紙張的曲線，而且錨定它指定的點集合。 在設計工具無法再建立曲線沿著曲線繪製與畫筆或鉛筆。 指定的點集合可能會產生不同的曲線，視實體曲線的內容。 例如，和彎曲的曲線會產生不同曲線比具有彈性的曲線。  
  
 讓所產生的數學曲線的曲線如下一次作業所產生的實體曲線的曲線數學曲線公式為基礎的彈性的木棍屬性。 就如同實體不同張力的曲線會產生不同的曲線，透過指定的點集合，數學曲線的張力參數不同的值將會產生不同曲線透過指定的點集合。 下圖顯示四個通過相同的一組點的基本曲線。 則會顯示每個曲線的張力。 張力 0 會對應至無限實體的張力，強迫曲線採取點之間最短的方式 （直線）。 張力 1 對應至任何實體的張力，允許曲線至少總彎曲的路徑。 張力值大於 1，曲線行為就像壓縮 spring，推送至需要較長的路徑。  
  
 ![基本曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 在上圖中的四個曲線共用相同的切線在起始點。 將正切函數是從起始點繪製到下一個點沿著曲線的線條。 同樣地，共用的正切函數結束點是曲線上繪製的結束點從先前的點的線條。  
  
 若要繪製基本曲線，您需要的執行個體<xref:System.Drawing.Graphics>類別， <xref:System.Drawing.Pen>，以及陣列<xref:System.Drawing.Point>物件的執行個體<xref:System.Drawing.Graphics>類別提供<xref:System.Drawing.Graphics.DrawCurve%2A>方法，這個方法會繪製曲線，和<xref:System.Drawing.Pen>儲存曲線，例如線條寬度和色彩的屬性。 陣列<xref:System.Drawing.Point>物件將會通過曲線的點。 下列程式碼範例顯示如何畫通過中點的基本曲線`myPointArray`。 第三個參數是張力。  
  
 [!code-csharp[LinesCurvesAndShapes#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>另請參閱  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [建構和繪製曲線](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
