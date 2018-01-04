---
title: "座標系統類型"
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 287b1c9eddef882041d9e4eac44a06190f3585a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="types-of-coordinate-systems"></a>座標系統類型
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]會使用三種座標空間： world、 頁面和裝置。 全局座標是用來建立模型特定的圖形範圍的座標，您將傳遞至方法在.NET Framework 中的座標。 頁面座標是指繪圖介面，例如表單或控制項所使用的座標系統。 裝置座標是實體裝置，例如螢幕或紙張繪製所使用的座標。 當您進行的呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，傳遞至的點<xref:System.Drawing.Graphics.DrawLine%2A>方法-`(0, 0)`和`(160, 80)`— 中全局座標空間。 之前[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以在螢幕上繪製線條，通過一連串的轉換的座標。 一個轉換，稱為全局轉換，將全局座標轉換為頁面座標和另一個轉換，稱為 「 頁面 」 轉換，將頁面座標轉換為裝置座標。  
  
## <a name="transforms-and-coordinate-systems"></a>轉換與座標系統  
 假設您想要搭配使用的原點本文工作區，而不是左上角的座標系統。 比方說，假設您想為 100 像素為單位，從工作區左邊緣和從用戶端區域的頂端 50 像素的原點。 下圖顯示這類的座標系統。  
  
 ![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 當您建立呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`，取得在下圖顯示的列。  
  
 ![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 三種座標空間中的程式行的結束點的座標如下所示：  
  
|||  
|-|-|  
|世界|（0，0） 到 160 (80）|  
|頁面|（100，50） 到 （260、 130）|  
|裝置|（100，50） 到 （260、 130）|  
  
 請注意，畫面座標空間原點左上角的 用戶端的區域。一律是這樣的情況。 也請注意，因為量值的單位為像素，裝置座標畫面座標相同。 如果您設定的度量單位為像素為單位 （例如英吋） 以外的項目，則裝置座標會不同於畫面座標。  
  
 全局轉換，以將全局座標對應頁面座標，保存在<xref:System.Drawing.Graphics.Transform%2A>屬性<xref:System.Drawing.Graphics>類別。 在上述範例中，自然變換是 x 方向的 100 個轉譯單位和 50 個單位，在 y 方向。 下列範例會設定的自然變換<xref:System.Drawing.Graphics>物件，並會使用該<xref:System.Drawing.Graphics>物件来繪製在上圖中顯示的列：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 頁面轉換會將頁面座標對應至裝置座標。 <xref:System.Drawing.Graphics>類別提供<xref:System.Drawing.Graphics.PageUnit%2A>和<xref:System.Drawing.Graphics.PageScale%2A>管理畫面轉換的屬性。 <xref:System.Drawing.Graphics>類別也提供兩個唯讀屬性，<xref:System.Drawing.Graphics.DpiX%2A>和<xref:System.Drawing.Graphics.DpiY%2A>，檢查水平和垂直 dpi 顯示裝置。  
  
 您可以使用<xref:System.Drawing.Graphics.PageUnit%2A>屬性<xref:System.Drawing.Graphics>類別，以指定的像素以外的測量單位。  
  
> [!NOTE]
>  您不能設定<xref:System.Drawing.Graphics.PageUnit%2A>屬性<xref:System.Drawing.GraphicsUnit.World>，因為這不是實體裝置，並會導致例外狀況。  
  
 下列範例會繪製線條，以從 （0，0） 到 （2，1），其中的點 （2，1） 是 2 英吋，向右和向下 1 英吋從點 （0，0）：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  如果您未指定畫筆寬度，當您建構您的畫筆時，上述範例中，會繪製為一英吋寬的線條。 您可以指定的第二個引數中的畫筆寬度<xref:System.Drawing.Pen>建構函式：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 如果我們假設顯示裝置，具有 96 dpi 的水平方向與 96 dpi 在垂直方向，在上述範例中線條的端點會有下列座標在三個座標空間：  
  
|||  
|-|-|  
|世界|（0，0） 到 （2，1）|  
|頁面|（0，0） 到 （2，1）|  
|裝置|(0，0，以 192 (96）|  
  
 請注意，因為全局座標空間的原點位於左上角的用戶端區域時，畫面座標全局座標相同。  
  
 您可以結合全局和頁面轉換，以達成各種不同的效果。 例如，假設您想要使用的測量單位為英吋，而您想從左邊緣起 2 英吋的 1/2 英吋，從用戶端區域的頂端與工作區座標系統的原點。 下列範例會設定全局和頁面轉換<xref:System.Drawing.Graphics>物件，並再繪製的直線 （0，0） 到 （2，1）：  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 下圖顯示的行和座標系統。  
  
 ![座標系統](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 如果我們假設顯示裝置，具有 96 dpi 的水平方向與 96 dpi 在垂直方向，在上述範例中線條的端點會有下列座標在三個座標空間：  
  
|||  
|-|-|  
|世界|（0，0） 到 （2，1）|  
|頁面|（2，0.5） 到 （4，1.5）|  
|裝置|（192，48） 到 （384、 144）|  
  
## <a name="see-also"></a>請參閱  
 [座標系統和轉換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [以矩陣來表示轉換](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
