---
title: HOW TO：建立線形漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: b836659821b54698b675d48acd4e46466001d654
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937883"
---
# <a name="how-to-create-a-linear-gradient"></a>HOW TO：建立線形漸層
GDI + 提供水平、 垂直和對角線形漸層。 根據預設，線性漸層色彩一致變更。 不過，您可以自訂的線性漸層，以便的色彩會變更以非統一的方式。  

> [!NOTE]
> 這篇文章中的範例是呼叫從控制項的方法<xref:System.Windows.Forms.Control.Paint>事件處理常式。  

下列範例填滿線條、 橢圓形和矩形，水平的線性漸層筆刷。  
  
<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>建構函式會收到四個引數： 兩個點和兩個色彩。 第一個點 （0，10） 相關聯的第一個色彩 （紅色），而第二點 （200，10） 的第二個色彩 （藍色） 與相關聯。 如您所預期，從所繪製的線條 （0，10） 到 （200，10） 會逐漸從紅色變成藍色。  
  
 在點 （0，10） 和 200 （10） 的 10 個不重要。 重要的是兩個點都有相同的第二個座標 — 它們連接的這條線是水平。 橢圓形和矩形也逐漸從紅色變成藍色，水平座標是從 0 到 200。  
  
 下圖顯示線條、 橢圓形和矩形。 請注意，之色彩漸層會自行重複增加超過 200 時的水平座標。  
  
 ![線性漸層](./media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>若要使用水平的線性漸層  
  
- 傳入的不透明的紅色及不透明藍色分別做為第三個和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 在上述範例中，，當您從水平座標 0 移到水平座標，為 200 的大小時色彩元件會以線性方式變更。 比方說，其第一個座標為偶數，介於 0 到 200 之間的點必須是介於 0 到 255 之間的中間的藍色元件。  
  
 GDI + 可讓您調整色彩之間而異的漸層的一個邊緣的方式。 假設您想要建立從黑色變成紅色，根據下表的漸層筆刷。  
  
|水平座標|RGB 元件|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 請注意，紅色元件在半強度時的水平座標是僅有百分之 20 的從 0 到 200 個的方式。  
  
 下列範例會設定<xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType>三個相對的位置與相關三個相對強度屬性。 如同上表中，為 0.5 的相對強度是 0.2 的相對位置相關聯。 橢圓形和漸層筆刷的矩形，會填滿的程式碼。  
  
 下圖顯示產生的橢圓形和矩形。  
  
 ![線性漸層](./media/cslineargradient2.png "cslineargradient2")  

### <a name="to-customize-linear-gradients"></a>若要自訂線性漸層  
  
- 傳入的不透明黑色及不透明的紅色分別做為第三個和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 在上述範例中的漸層已水平;也就是，色彩會逐漸當您移動任何水平對齊。 您也可以定義垂直漸層和對角線的漸層。  
  
 下列範例會將點 （0，0） 和 （200，100） 傳遞給<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>建構函式。 藍色相關聯 （0，0） 和相關聯的綠色 （200，100）。 （包含畫筆寬度為 10） 的線條和 ellipse 會以線性漸層筆刷填滿。  
  
 下圖顯示的一行，並省略符號。 請注意，在 ellipse 變更色彩逐漸沿著任何移動線是兩點的直線通過 （0，0） 和 （200，100）。  
  
 ![線性漸層](./media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>若要建立對角線的線性漸層  
  
- 傳入的不透明的藍色及不透明綠色分別做為第三個和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>另請參閱

- [使用漸層筆刷填滿形狀](using-a-gradient-brush-to-fill-shapes.md)
- [Windows Forms 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
