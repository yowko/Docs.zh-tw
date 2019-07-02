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
ms.openlocfilehash: 66061341ee6539e2172c537a0b2a6ec9ff87565c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506116"
---
# <a name="alpha-blending-lines-and-fills"></a>Alpha 混色線條和填色
在 GDI + 中，色彩會是 8 位元每個 alpha、 紅色、 綠色和藍色的 32 位元值。 Alpha 值，表示色彩的透明度，範圍的色彩會與背景的色彩混合。 從 0 到 255，其中 0 代表完全透明的色彩，到 255 的 alpha 值範圍表示完全不透明的色彩。  
  
 Alpha 透明混色是像素 x 像素的混合，其來源和背景的色彩資料。 每個指定之來源色彩的三個元件 （紅色、 綠色、 藍色） 會混合使用之對應元件的背景色彩，根據下列公式：  
  
 displayColor = sourceColor × alpha / 255 + backgroundColor × (255-alpha) / 255  
  
 例如，假設來源色彩中的紅色元件是 150，背景色彩中的紅色元件是 100。 如果 alpha 值為 200，產生的色彩中紅色元件的計算方式如下：  
  
 150 × 200 / 255 + 100 × (255 – 200) / 255 = 139  
  
## <a name="in-this-section"></a>本節內容  
 [如何：繪製不透明和半透明線條](how-to-draw-opaque-and-semitransparent-lines.md)  
 示範如何繪製 alpha 混色線條。  
  
 [如何：使用不透明和半透明筆刷繪製](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 說明如何使用筆刷的 alpha-混用。  
  
 [如何：使用複合模式控制 Alpha 混色](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 描述如何控制使用 alpha 透明混色<xref:System.Drawing.Drawing2D.CompositingMode>。  
  
 [如何：使用色彩矩陣設定影像中的 Alpha 值](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 說明如何使用<xref:System.Drawing.Imaging.ColorMatrix>物件，以控制 alpha 混色。
