---
title: "如何：將曲線路徑簡維為線條"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], flattening curves into lines
- curves [Windows Forms], flattening
- GraphicsPath object
- paths [Windows Forms], flattening
- drawing [Windows Forms], flattening curves
ms.assetid: e654b8de-25f4-4735-9208-42e4514a589c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 334fc0fee7166f8f8c5c1db61d3b9e370da72f87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-flatten-a-curved-path-into-a-line"></a>如何：將曲線路徑簡維為線條
A<xref:System.Drawing.Drawing2D.GraphicsPath>物件會儲存一連串的線路與貝茲曲線。 您可以加入幾種類型的曲線 （省略符號、 弧線、 曲線） 的路徑，但之前儲存的路徑中，將會轉換成貝茲曲線的每個曲線。 簡維路徑包含將在路徑中的每個貝茲曲線轉換成一系列直線。 下圖顯示路徑之前和之後扁平化。  
  
 ![直線和曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art32a.gif "AboutGdip02_Art32A")  
  
### <a name="to-flatten-a-path"></a>壓平合併路徑  
  
-   呼叫<xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法<xref:System.Drawing.Drawing2D.GraphicsPath>物件。 <xref:System.Drawing.Drawing2D.GraphicsPath.Flatten%2A>方法會接收指定的原始路徑簡維的路徑之間的最大距離為扁平引數。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [建構和繪製路徑](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
