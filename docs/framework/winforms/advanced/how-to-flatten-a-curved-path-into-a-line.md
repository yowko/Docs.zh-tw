---
title: HOW TO：將曲線路徑壓平合併為線條
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
ms.openlocfilehash: a151b4244e14d3704fd5fa1c55de92211981232f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781340"
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>HOW TO：將曲線路徑壓平合併為線條
A<xref:System.Drawing.Drawing2D.GraphicsPath>物件會儲存一串線和貝茲曲線。 您可以將數種類型的曲線 （省略符號，弧線，基線曲線） 加入路徑，但之前它會儲存在路徑中的每條曲線轉換成貝茲曲線。 壓平合併的路徑將每個路徑中的貝茲曲線轉換成一連串的直線，線條所組成。 壓平合併的前後，如下圖所顯示的路徑。  
  
 ![直線和曲線](./media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>若要壓平合併的路徑  
  
- 呼叫<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法的<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法會接收指定的扁平化的路徑與原始路徑之間的最大距離的扁平引數。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [建構和繪製路徑](constructing-and-drawing-paths.md)
