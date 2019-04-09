---
title: 座標系統類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: 765df4bcd3cef83e624ad8b11676696b95f7d035
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089298"
---
# <a name="types-of-coordinate-systems"></a>座標系統類型
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 使用三個座標空間： 世界、 頁面和裝置。 全局座標是用來建立模型為特定圖形範圍的座標，您將傳遞給方法，在.NET Framework 中的座標。 頁面座標是指繪圖介面，例如表單或控制項所使用的座標系統。 裝置座標是實體裝置上，繪製到螢幕或紙張等所使用的座標。 當您進行呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，您將傳遞至的點<xref:System.Drawing.Graphics.DrawLine%2A>方法 —`(0, 0)`和`(160, 80)`— 全局座標空間中。 之前[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以在螢幕上繪製線條、 座標通過一連串的轉換。 一個轉換，稱為 「 世界 」 轉換中，將全局座標轉換成頁面座標，以及另一個轉換，稱為 「 頁面 」 轉換中，將轉換成頁面座標裝置座標。  
  
## <a name="transforms-and-coordinate-systems"></a>轉換和座標系統  
 假設您想要使用的工作區，而不是左上角的主體中原點座標系統。 例如，假設您想要從工作區左邊緣的 100 像素且從工作區頂端的 50 個像素的原點。 下圖顯示這類的座標系統。  
  
 ![座標系統](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 當您建立呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，取得在下圖中顯示的列。  
  
 ![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 您的企業中的三個座標空間的端點座標如下所示：  
  
|||  
|-|-|  
|世界|（0，0） 到 160 (80）|  
|頁面|（100，50） 到 （260、 130）|  
|裝置|（100，50） 到 （260、 130）|  
  
 請注意頁面座標空間的原點，左上角的 用戶端的區域。這一律會是大小寫。 也請注意，測量單位為像素，因為裝置座標畫面座標相同。 如果您將為測量單位為像素為單位 （例如英吋） 以外的項目時，裝置座標會不同於畫面座標。  
  
 全局轉換，可將全局座標對應成頁面座標，會保留在<xref:System.Drawing.Graphics.Transform%2A>屬性<xref:System.Drawing.Graphics>類別。 在上述範例中，全局轉換是在 x 方向轉譯 100 單位並在 y 方向的 50 個單位。 下列範例會設定的自然變換<xref:System.Drawing.Graphics>物件，並會使用該<xref:System.Drawing.Graphics>物件来繪製在上圖中顯示的列：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 「 頁面 」 轉換會將頁面座標對應至裝置座標。 <xref:System.Drawing.Graphics>類別會提供<xref:System.Drawing.Graphics.PageUnit%2A>和<xref:System.Drawing.Graphics.PageScale%2A>操作 「 頁面 」 轉換的屬性。 <xref:System.Drawing.Graphics>類別也會提供兩個唯讀屬性，<xref:System.Drawing.Graphics.DpiX%2A>和<xref:System.Drawing.Graphics.DpiY%2A>，檢查水平和垂直 dpi 為單位的顯示裝置。  
  
 您可以使用<xref:System.Drawing.Graphics.PageUnit%2A>屬性<xref:System.Drawing.Graphics>類別，以指定的像素以外的量值單位。  
  
> [!NOTE]
>  您無法設定<xref:System.Drawing.Graphics.PageUnit%2A>屬性設<xref:System.Drawing.GraphicsUnit.World>，因為這不是實體單位，並會導致例外狀況。  
  
 下列範例會繪製線條，以從 （0，0） 到 （2，1），其中 （2，1） 的點是 2 英吋為單位向右再向下 1 英吋從點 （0，0）：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  如果您未指定畫筆寬度，當您建構您的畫筆時，上述範例會繪製為一英吋寬的線條。 您可以指定的第二個引數中的畫筆寬度<xref:System.Drawing.Pen>建構函式：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 如果我們假設在顯示裝置，有 96 dpi 的水平方向和 96 dpi 為單位，在垂直方向，在上述範例中線條的端點會有下列的座標，三個座標空間中：  
  
|||  
|-|-|  
|世界|（0，0） 到 （2，1）|  
|頁面|（0，0） 到 （2，1）|  
|裝置|(0，0，到 （192，96）|  
  
 請注意，因為全局座標空間的原點位於左上角的 工作區時，畫面座標的全局座標相同。  
  
 您可以結合的全局和頁面轉換，來達到各種不同的效果。 比方說，假設您想要做為測量單位為英吋為單位，而您想要為 2 英吋為單位從左邊緣的工作區和 1/2 英吋，從用戶端區域的頂端座標系統的原點。 下列範例會設定全局和頁面轉換<xref:System.Drawing.Graphics>物件，並再分別繪製一條從 （0，0） 到 （2，1）：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 下圖顯示的行和座標系統。  
  
 ![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 如果我們假設在顯示裝置，有 96 dpi 的水平方向和 96 dpi 為單位，在垂直方向，在上述範例中線條的端點會有下列的座標，三個座標空間中：  
  
|||  
|-|-|  
|世界|（0，0） 到 （2，1）|  
|頁面|（2，0.5） 到 （4，1.5）|  
|裝置|（192，48） 到 （384，第 144）|  
  
## <a name="see-also"></a>另請參閱

- [座標系統和轉換](coordinate-systems-and-transformations.md)
- [以矩陣來表示轉換](matrix-representation-of-transformations.md)
