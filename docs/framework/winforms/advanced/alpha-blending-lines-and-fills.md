---
title: Alpha 混色線條和填色
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: f58fa2d105492c6c72d3d6906c3c35f89130fe91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517682"
---
# <a name="alpha-blending-lines-and-fills"></a>Alpha 混色線條和填色
在[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，色彩是與 8 位元每個 alpha、 紅、 綠和藍 32 位元值。 Alpha 值表示色彩的透明度，以背景色彩的色彩會混合的範圍。 從 0 到 255，其中 0 代表完全透明的色彩，到 255 的 alpha 值範圍表示完全不透明的色彩。  
  
 Alpha 混色是像素 x 像素的混合，其來源和背景的色彩資料。 每個指定的來源色彩的三個元件 （紅色、 綠色、 藍色） 會混合使用對應元件的背景色彩，根據下列公式：  
  
 displayColor = sourceColor × alpha / 255 + backgroundColor × (255-alpha) / 255  
  
 例如，假設來源色彩的紅色元件是 150，而背景色彩的紅色元件為 100。 如果 alpha 值是 200，產生色彩的紅色元件的計算方式如下：  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>本節內容  
 [操作說明：繪製不透明和半透明線條](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 示範如何繪製 alpha 混色線條。  
  
 [操作說明：使用不透明和半透明筆刷繪製](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 說明如何 alpha-blend 的筆刷。  
  
 [操作說明：使用複合模式控制 Alpha 混色](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 描述如何控制 alpha 混色使用<xref:System.Drawing.Drawing2D.CompositingMode>。  
  
 [操作說明：使用色彩矩陣設定影像中的 Alpha 值](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 說明如何使用<xref:System.Drawing.Imaging.ColorMatrix>物件來控制 alpha 混色。
