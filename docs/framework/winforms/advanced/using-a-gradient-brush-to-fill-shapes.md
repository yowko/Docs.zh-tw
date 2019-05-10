---
title: 使用漸層筆刷填滿形狀
ms.date: 03/30/2017
helpviewer_keywords:
- brushes [Windows Forms], gradient brushes
- gradient brushes
- examples [Windows Forms], gradient brushes
ms.assetid: 2c6037b9-05bd-44c0-a22a-19584b722524
ms.openlocfilehash: 7ff555ba4fd81e9123e5f9e9feed38a0ec9d0a08
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063603"
---
# <a name="using-a-gradient-brush-to-fill-shapes"></a>使用漸層筆刷填滿形狀
您可以使用漸層筆刷填滿圖形，以逐漸變更色彩。 例如，您可以使用水平漸層來填滿色彩，當您從圖形的左邊緣移至 右邊緣會逐漸變更形狀。 假設有一個矩形，為黑色的左邊緣 （以紅色、 綠色和藍色元件 0，0，0） 和右邊緣是 red （由 255，0，0）。 如果矩形是 256 像素寬，給定的像素的紅色元件將會大於其左邊的像素的紅色元件。 資料列中最左邊的像素色彩元件 （0，0，0）、 第二個像素具有 （1，0，0），第三個像素的 （2，0，0），並依此類推，直到到達最右邊像素的色彩元件 （255，0，0）。 這些內插補點的色彩值會產生之色彩漸層。  
  
 當您移動水平、 垂直，或指定斜線平行線形漸層會變更色彩。 當您移動相關的內部和路徑的邊界色彩變更路徑漸層。 您可以自訂路徑漸層來達到各種不同的效果。  
  
 下圖顯示以線性漸層筆刷填滿的矩形和路徑的漸層筆刷填滿橢圓形：  
  
 ![矩形填滿橢圓形使用的漸層筆刷。](./media/using-a-gradient-brush-to-fill-shapes/rectangle-ellipse-gradient-brush.png)  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立線形漸層](how-to-create-a-linear-gradient.md)  
 示範如何使用下列方法建立線性漸層停駐<xref:System.Drawing.Drawing2D.LinearGradientBrush>類別。  
  
 [如何：建立路徑漸層](how-to-create-a-path-gradient.md)  
 描述如何建立路徑漸層停駐 using<xref:System.Drawing.Drawing2D.PathGradientBrush>類別。  
  
 [如何：將 Gamma 修正套用至漸層](how-to-apply-gamma-correction-to-a-gradient.md)  
 說明如何使用漸層筆刷的 gamma 修正。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>  
 包含描述此類別並且連結到其所有成員。  
  
 <xref:System.Drawing.Drawing2D.PathGradientBrush?displayProperty=nameWithType>  
 包含描述此類別並且連結到其所有成員。
