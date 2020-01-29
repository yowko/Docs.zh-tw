---
title: 相
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: c95888f31bfc867e9c028d53072ab3d710256708
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734671"
---
# <a name="windows-forms-coordinates"></a>Windows Form 座標
Windows Form 的座標系統是以裝置座標為基礎，而在 Windows Forms 中繪製時的基本測量單位是裝置單位（通常是圖元）。 螢幕上的點是由 x 和 y 座標配對所描述，而 x 座標則是靠右遞增，而 y 座標則是從上到下遞增。 相對於螢幕的原點位置會根據您指定的是畫面或用戶端座標而有所不同。  
  
## <a name="screen-coordinates"></a>螢幕座標  
 Windows Forms 應用程式會以螢幕座標指定視窗在螢幕上的位置。 針對螢幕座標，原點是螢幕的左上角。 視窗的完整位置通常是由包含兩個點之螢幕座標（定義視窗的左上角和右下角）的 <xref:System.Drawing.Rectangle> 結構所描述。  
  
## <a name="client-coordinates"></a>用戶端座標  
 Windows Forms 應用程式會使用用戶端座標指定表單或控制項中的點位置。 用戶端座標的原點是控制項或表單工作區的左上角。 用戶端座標可確保應用程式在表單或控制項中繪製時，可以使用一致的座標值，不論表單或控制項在螢幕上的位置為何。  
  
 工作區的維度也會由包含該區域之用戶端座標的 <xref:System.Drawing.Rectangle> 結構所描述。 在所有情況下，矩形的左上角座標會包含在工作區中，而在右下方的座標則會排除。 圖形作業不包含工作區的右和下邊緣。 例如，<xref:System.Drawing.Graphics.FillRectangle%2A> 方法會填滿指定矩形的右邊和下邊緣，但不會包含這些邊緣。  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>從一個座標類型對應到另一個  
 有時候，您可能需要從螢幕座標組應到用戶端座標。 您可以使用 <xref:System.Windows.Forms.Control> 類別提供的 <xref:System.Windows.Forms.Control.PointToClient%2A> 和 <xref:System.Windows.Forms.Control.PointToScreen%2A> 方法，輕鬆完成這項操作。 例如，<xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.MousePosition%2A> 屬性會以螢幕座標回報，但您可能會想要將這些內容轉換成用戶端座標。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
