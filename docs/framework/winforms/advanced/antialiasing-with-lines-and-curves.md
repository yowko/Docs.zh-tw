---
title: "線條和曲線的反鋸齒功能"
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
- antialiasing
- antialiasing [Windows Forms], smoothing modes
- GDI+, antialiasing
ms.assetid: 810da1a4-c136-4abf-88df-68e49efdd8d4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8552f185a93b688555dbcfab3da9d28d9bfde6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="antialiasing-with-lines-and-curves"></a>線條和曲線的反鋸齒功能
當您使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]繪製一條線，您提供的起點和結束點的行，但您沒有提供在列上的任何資訊的個別像素。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]顯示驅動程式軟體，以判斷哪一個像素為單位將會開啟以特定顯示裝置上顯示線與搭配運作。  
  
## <a name="aliasing"></a>別名  
 請考慮直接紅線，會從點 （4，2） 移至的點 （16，10）。 假設座標系統的原點位於左上角和度量單位為像素。 也假設，x 軸指向右側，而 y 軸向下。 下圖顯示彩色的背景上繪製紅線放大的的檢視。  
  
 ![線條，無反鋸齒](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art33.gif "AboutGdip02_Art33")  
  
 用來呈現線條的紅色像素是不透明的。 行中有不透明的像素。 這種類型的行呈現所產生的線條不規則的外觀，並看起來有點像階梯。 代表的階梯線條的這項技術稱為別名。階梯是理論行的別名。  
  
## <a name="antialiasing"></a>反鋸齒功能  
 繪製線條更趨精密完美的技術包含使用透明的像素，以及不透明的像素為單位。 像素為單位設定為純紅色，或紅和背景色彩混合體，根據如何關閉它們是列。 這種類型的呈現稱為反鋸齒功能，而導致人類的眼睛感知為更平滑線。 下圖顯示如何在背景產生鋸齒線條與混合特定像素為單位。  
  
 ![消除鋸齒線條](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art34.gif "AboutGdip02_Art34")  
  
 反鋸齒功能，也稱為 平滑，也可以套用至曲線。 下圖顯示放大平滑的橢圓形的檢視。  
  
 ![消除鋸齒曲線](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art35.gif "AboutGdip02_Art35")  
  
 下圖顯示相同的橢圓形的實際大小，一次進行反鋸齒處理而一次使用反鋸齒功能。  
  
 ![反鋸齒功能範例](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art36.gif "AboutGdip02_Art36")  
  
 若要繪製的直線和曲線使用消除鋸齒，建立的執行個體<xref:System.Drawing.Graphics>類別並設定其<xref:System.Drawing.Graphics.SmoothingMode%2A>屬性<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>或<xref:System.Drawing.Drawing2D.SmoothingMode.HighQuality>。 然後呼叫其中一個繪圖的方法相同<xref:System.Drawing.Graphics>類別。  
  
 [!code-csharp[LinesCurvesAndShapes#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#81)]
 [!code-vb[LinesCurvesAndShapes#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#81)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Drawing.Drawing2D.SmoothingMode?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [操作說明：使用文字反鋸齒功能](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)
