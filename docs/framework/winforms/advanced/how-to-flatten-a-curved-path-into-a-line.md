---
title: HOW TO：曲線的路徑簡維的線條
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: aa47a655417cdf82d79fb222dc6ff6f6d8c3a947
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601814"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>HOW TO：曲線的路徑簡維的線條
A<xref:System.Drawing.Drawing2D.GraphicsPath>物件會儲存一串線和貝茲曲線。 您可以將數種類型的曲線 （省略符號，弧線，基線曲線） 加入路徑，但之前它會儲存在路徑中的每條曲線轉換成貝茲曲線。 壓平合併的路徑將每個路徑中的貝茲曲線轉換成一連串的直線，線條所組成。 壓平合併的前後，如下圖所顯示的路徑。  
  
 ![直線和曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>若要壓平合併的路徑  
  
-   呼叫<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法的<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法會接收指定的扁平化的路徑與原始路徑之間的最大距離的扁平引數。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
