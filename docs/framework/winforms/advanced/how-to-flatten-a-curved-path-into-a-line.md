---
title: 如何：將曲線路徑簡維為線條
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a3a8467dc5906a88911672316bb0f2ed3607d3a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>如何：將曲線路徑簡維為線條
A<xref:System.Drawing.Drawing2D.GraphicsPath>物件會儲存一連串的線路與貝茲曲線。 您可以加入幾種類型的曲線 （省略符號、 弧線、 曲線） 的路徑，但之前儲存的路徑中，將會轉換成貝茲曲線的每個曲線。 簡維路徑包含將在路徑中的每個貝茲曲線轉換成一系列直線。 下圖顯示路徑之前和之後扁平化。  
  
 ![直線和曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>壓平合併路徑  
  
-   呼叫<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法會接收指定的原始路徑簡維的路徑之間的最大距離為扁平引數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
