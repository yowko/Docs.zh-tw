---
title: GDI+ 中的基本曲線
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], cardinal
- GDI+, cardinal splines
- cardinal splines
ms.assetid: 09b3797a-6294-422d-9adf-a5a0a7695c0c
ms.openlocfilehash: 4588f6f606f0f479aeae1d143f23175ec4be32a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200411"
---
# <a name="cardinal-splines-in-gdi"></a>GDI+ 中的基本曲線
基本曲線是一連串個別加入形成更大的曲線的曲線。 指定曲線的點和張力參數陣列。 中的陣列; 每個點順利通過的基本曲線有沒有尖角和中的曲線 tightness 任何突然的變更。 下圖顯示一組點和通過集合中的每個點的基本曲線。  
  
 ![基本曲線](./media/aboutgdip02-art09.gif "Aboutgdip02_art09")  
  
## <a name="physical-and-mathematical-splines"></a>實體和數學的曲線  
 實體的曲線是精簡的一種 wood 或其他具彈性的資料。 之前的數學曲線問世，設計工具會用來繪製曲線實體曲線。 設計工具會置於一張紙的曲線和它錨定至一組指定的點。 設計工具無法再建立曲線沿著曲線繪製與畫筆或鉛筆。 一組指定的點可能會產生各種不同的曲線的曲線實體的屬性而定。 比方說，高度的抵抗彎曲的曲線會產生不同的曲線比極具彈性的曲線。  
  
 數學曲線的公式根據彈性敲的屬性，因此所產生的數學曲線的曲線會類似於一次所產生之實體的曲線的曲線。 如同實體曲線的張力不同會產生不同的曲線，透過一組指定的點，數學曲線的張力參數不同的值將會產生不同的曲線，透過指定的點集合。 下圖顯示四個基本的曲線，通過相同的一組點。 每個曲線的張力會顯示。 0 的張力會對應至無限實體的張力，強制要花點之間最短的方式 （直線） 的曲線。 張力 1 會對應至任何實體的張力，讓曲線使用至少總彎曲的路徑。 張力值大於 1，曲線的行為類似壓縮的 spring，推送到較長的路徑。  
  
 ![基本曲線](./media/aboutgdip02-art10.gif "Aboutgdip02_art10")  
  
 在上圖中的四條曲線共用相同的切線的開始點。 正切函數是從起始點繪製到下一個點沿著曲線的線條。 同樣地，共用的正切函數結束點是從結束點繪製到先前的點在曲線上的線條。  
  
 若要繪製基本曲線，您需要的執行個體<xref:System.Drawing.Graphics>類別， <xref:System.Drawing.Pen>，和陣列<xref:System.Drawing.Point>物件的執行個體<xref:System.Drawing.Graphics>類別會提供<xref:System.Drawing.Graphics.DrawCurve%2A>方法，會繪製曲線，和<xref:System.Drawing.Pen>儲存曲線，例如線條寬度和色彩的屬性。 陣列<xref:System.Drawing.Point>物件將會通過曲線的點。 下列程式碼範例示範如何繪製基本曲線中的點為通過`myPointArray`。 第三個參數是張力。  
  
 [!code-csharp[LinesCurvesAndShapes#31](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#31)]
 [!code-vb[LinesCurvesAndShapes#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>另請參閱

- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [建構和繪製曲線](constructing-and-drawing-curves.md)
