---
title: Windows Form 座標
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: 6feabadff17538f4a7368c348f7b72226e2d678e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59980651"
---
# <a name="windows-forms-coordinates"></a>Windows Form 座標
在 Windows Form 座標系統根據裝置座標和量值在 Windows Form 中描繪時的基本單位是裝置單位 （一般而言，像素）。 在螢幕上的點的 x 和 y 座標組說明增加到右並增加從上往下 y 座標的 x 座標。 相對於畫面中，原點的位置會因您指定螢幕或用戶端座標。  
  
## <a name="screen-coordinates"></a>螢幕座標  
 在 Windows Forms 應用程式在螢幕座標的畫面上，指定視窗的位置。 螢幕座標，原點是畫面的左上角。 完整視窗的位置，通常藉由描述<xref:System.Drawing.Rectangle>結構，其中包含定義視窗的左上角和右下角邊角的兩個點的螢幕座標。  
  
## <a name="client-coordinates"></a>工作區座標  
 在 Windows Forms 應用程式在表單或控制項使用用戶端座標指定點的位置。 工作區座標中的來源是控制項或表單的工作區的左上角。 用戶端座標可確保應用程式表單或控制項，不論表單或螢幕上的控制項的位置中繪製時可以使用一致的座標值。  
  
 用戶端區域的維度也會描述<xref:System.Drawing.Rectangle>結構，包含區域的座標。 在所有情況下，矩形的左上角座標包含在工作區中，雖然已排除的右下座標。 圖形作業不會包含右和下邊緣的工作區。 例如<xref:System.Drawing.Graphics.FillRectangle%2A>方法會填滿指定的矩形的右邊緣與下緣，但不是包括這些邊緣。  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>從一種類型的座標對應至另一個  
 有時候，您可能需要從螢幕座標對應至用戶端座標。 您可以使用，輕鬆地完成這<xref:System.Windows.Forms.Control.PointToClient%2A>並<xref:System.Windows.Forms.Control.PointToScreen%2A>方法，可<xref:System.Windows.Forms.Control>類別。 比方說，<xref:System.Windows.Forms.Control.MousePosition%2A>屬性<xref:System.Windows.Forms.Control>回報在螢幕座標中，但您可能想要將這些座標轉換。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.PointToClient%2A>
- <xref:System.Windows.Forms.Control.PointToScreen%2A>
