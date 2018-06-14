---
title: Windows Form 座標
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
ms.openlocfilehash: ba6bf8c1a8ae5ab14a9b33ae431e34310046b2a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537872"
---
# <a name="windows-forms-coordinates"></a>Windows Form 座標
Windows form 座標系統為基礎裝置座標和量值時，在 Windows Form 中描繪的基本單位是裝置單位 （一般而言，像素）。 在螢幕上的點以 x 和 y 座標組說明增加到右、 增加從上到下 y 座標的 x 座標。 相對於螢幕的原點的位置會因您指定螢幕或用戶端座標。  
  
## <a name="screen-coordinates"></a>螢幕座標  
 Windows Form 應用程式在螢幕座標的畫面上，指定視窗的位置。 螢幕座標，來源為螢幕左上角。 完整視窗的位置，通常由描述<xref:System.Drawing.Rectangle>結構包含兩個控制點會定義視窗的左上角和右下角的螢幕座標。  
  
## <a name="client-coordinates"></a>用戶端座標  
 Windows Form 應用程式在表單或控制項使用用戶端座標指定點的位置。 工作區座標的原點是控制項或表單的工作區的左上角。 用戶端座標可確保應用程式可以在表單或控制項，不論表單或螢幕上的控制項的位置繪製時使用一致的座標值。  
  
 用戶端區域的維度也會描述<xref:System.Drawing.Rectangle>結構，其中包含用戶端區域的座標。 在所有情況下，矩形左上角座標隨附於用戶端區域中，但是會排除右下角座標。 圖形作業不會包含右邊緣和下邊緣的工作區。 例如<xref:System.Drawing.Graphics.FillRectangle%2A>方法就會填滿指定的矩形的右邊緣與下邊緣，但不是包括這些邊緣。  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a>對應到另一種類型的座標  
 有時候您可能需要從螢幕座標對應至用戶端座標。 您可以輕鬆地完成這項作業使用<xref:System.Windows.Forms.Control.PointToClient%2A>和<xref:System.Windows.Forms.Control.PointToScreen%2A>中可用的方法<xref:System.Windows.Forms.Control>類別。 比方說，<xref:System.Windows.Forms.Control.MousePosition%2A>屬性<xref:System.Windows.Forms.Control>回報在螢幕座標中，但您可能想要將這些轉換成用戶端座標。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
