---
title: "如何：建立線形漸層"
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
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbf3b1657a5a6b91ba88a0968b6b92d4e4bdbf0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linear-gradient"></a>如何：建立線形漸層
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供水平、 垂直和對角線線形漸層。 根據預設，線性漸層色彩一致變更。 不過，您可以自訂線性漸層，以便以非統一的方式變更色彩。  
  
 下列範例會填滿線條、 橢圓形和矩形，水平的線性漸層筆刷。  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>建構函式會收到四個引數： 兩個點和兩個色彩。 第一個點 （0，10） 的第一個色彩 （紅色），與相關聯，且 （200，10） 的第二個點都與第二個色彩 （藍色）。 如您所預期，從繪製 （0，10） 到 200 (10） 會逐漸從紅色為藍色。  
  
 在點 （50，10） 和 200 （10） 10s 不是重要的。 重要的是兩個點都有相同的第二個座標： 連接它們的直線是水平。 橢圓形和矩形也逐漸從變更為藍色的水平座標是從 0 到 200 為紅色。  
  
 下圖顯示線條、 橢圓形和矩形。 請注意，色彩漸層會自行重複，增加超過 200 時的水平座標。  
  
 ![線性漸層](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>若要使用水平的線性漸層  
  
-   傳入的不透明的紅色的且不透明藍色分別做為第三個和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 在上述範例中，色彩元件變更以線性方式從水平座標 0 移到 200 水平座標。 比方說，其第一個座標為偶數，介於 0 到 200 之間的點必須是介於 0 和 255 的藍色元件。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可讓您調整色彩更改一邊漸層的其他方式。 假設您想要建立從黑色變成紅色，根據下表的漸層筆刷。  
  
|水平座標|RGB 元件|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 請注意，紅色元件半濃度時的水平座標是僅有百分之 20 的方式從 0 到 200 個。  
  
 下列範例會設定<xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A>屬性<xref:System.Drawing.Drawing2D.LinearGradientBrush>三個相對強度與三個的相對位置的物件。 如同上表中，0.5 的相對強度為 0.2 相對位置與相關聯。 程式碼填滿橢圓形和矩形漸層筆刷。  
  
 下圖顯示產生的橢圓形和矩形。  
  
 ![線性漸層](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### <a name="to-customize-linear-gradients"></a>若要自訂線形漸層  
  
-   傳入的不透明的黑色和不透明紅色分別做為第三個和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 前述範例中的漸層已水平。亦即，色彩會逐漸當您移動任何水平對齊。 您也可以定義垂直漸層和對角線漸層。  
  
 下列範例會將點 （0，0） 和 （200，100） 傳遞至<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A>建構函式。 藍色相關聯 （0，0） 和相關聯的綠色 （200，100）。 直線 （畫筆寬度為 10） 和一個橢圓形會填入線性漸層筆刷。  
  
 下圖顯示的一行，並省略符號。 請注意中的省略符號變更色彩逐漸當您移動任何沿著線是平行處理通過列 （0，0） 和 （200，100）。  
  
 ![線性漸層](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>若要建立對角線線形漸層  
  
-   傳入的不透明的藍色和不透明綠色分別做為第三個和第四個引數。  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>另請參閱  
 [使用漸層筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
