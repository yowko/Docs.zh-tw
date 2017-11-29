---
title: "使用漸層筆刷填滿形狀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a1c4ab7c2ee6f7164b6158dcb4ca4721be12650
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>使用漸層筆刷填滿形狀
您可以使用漸層筆刷填滿圖形的逐漸變更的色彩。 例如，您可以使用水平漸層來填滿色彩逐漸變更在左邊緣圖案移右邊緣的形狀。 假設有一個矩形，為黑色的左邊緣 （代表紅色、 綠色和藍色元件 0，0，0） 和右邊緣是紅色 （由 255，0，0）。 如果矩形是 256 像素寬，給定的像素的紅色元件將會大於其左側的像素的紅色元件。 資料列中最左邊的像素會有色彩元件 （0，0，0）、 第二個像素 （1，0，0），第三個像素的 （2，0，0），並依此類推，直到到達最右邊像素的色彩元件 （255，0，0）。 這些插補的色彩值便會產生之色彩漸層。  
  
 當您移動水平、 垂直，或指定斜線平行色彩變更線形漸層。 路徑漸層變更色彩，當您移動需內部和路徑的界限。 您可以自訂路徑漸層來達到各種不同的效果。  
  
 下圖顯示以線性漸層筆刷填滿的矩形和橢圓形填入路徑漸層筆刷。  
  
 ![漸層停駐](../../../../docs/framework/winforms/advanced/media/gradient2.png "gradient2")  
  
## <a name="in-this-section"></a>本章節內容  
 [操作說明：建立線性漸層](../../../../docs/framework/winforms/advanced/how-to-create-a-linear-gradient.md)  
 示範如何建立線形漸層停駐 using<xref:System.Drawing.Drawing2D.LinearGradientBrush>類別。  
  
 [操作說明：建立路徑漸層](../../../../docs/framework/winforms/advanced/how-to-create-a-path-gradient.md)  
 描述如何建立路徑漸層停駐 using<xref:System.Drawing.Drawing2D.PathGradientBrush>類別。  
  
 [操作說明：將 Gamma 修正套用至漸層](../../../../docs/framework/winforms/advanced/how-to-apply-gamma-correction-to-a-gradient.md)  
 說明如何使用漸層筆刷的 gamma 修正。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 包含這個類別的描述，並且提供其所有成員的連結。  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 包含這個類別的描述，並且提供其所有成員的連結。
