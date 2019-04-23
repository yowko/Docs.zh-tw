---
title: HOW TO：從直線、曲線和形狀建立圖形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
ms.openlocfilehash: eeaf478375e08734b20d83b6f3c8030732495013
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224906"
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a>HOW TO：從直線、曲線和形狀建立圖形
若要建立圖表，建構<xref:System.Drawing.Drawing2D.GraphicsPath>，然後呼叫方法，例如<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>和<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>，以新增至路徑的基本項目。  
  
## <a name="example"></a>範例  
 下列程式碼範例會建立含有圖形的路徑：  
  
-   第一個範例會建立包含單一圖形的路徑。 此圖是由單一弧形所組成。弧線有的掃掠角度-180 度，也就是預設座標系統中的 逆時鐘方向。  
  
-   第二個範例會建立具有兩個圖形的路徑。 第一個圖形是後面接著行弧形。 第二張圖是後面接著曲線，後面接著行。 第一個圖形會處於開啟狀態，而且第二張圖會關閉。  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 先前的範例專為搭配 Windows Form 使用，而且它們需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Drawing2D.GraphicsPath>
- [建構和繪製路徑](constructing-and-drawing-paths.md)
- [使用畫筆繪製線條和形狀](using-a-pen-to-draw-lines-and-shapes.md)
