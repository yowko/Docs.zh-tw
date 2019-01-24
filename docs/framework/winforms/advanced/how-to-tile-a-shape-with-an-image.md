---
title: HOW TO：並排顯示影像與圖案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
ms.openlocfilehash: f2edde7e78f996d4a7bfbc636210f315c0718f6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693209"
---
# <a name="how-to-tile-a-shape-with-an-image"></a>HOW TO：並排顯示影像與圖案
如同可以彼此討論 floor 旁邊放圖格，可以彼此相鄰放矩形的映像，來填滿 (tile) 圖形。 若要並排顯示圖案的內部，使用紋理筆刷。 當您建構<xref:System.Drawing.TextureBrush>物件時，您將傳遞至建構函式的引數之一<xref:System.Drawing.Image>物件。 當您使用的材質筆刷來繪製圖形的內部時，圖形會填入此映像的重複副本。  
  
 自動換行模式屬性<xref:System.Drawing.TextureBrush>物件可以決定如何將映像為導向重複矩形格線中。 您可以進行所有的磚，在方格中有相同的方向，或您可從一個格線位置翻轉至下一個映像。 翻轉為水平、 垂直或兩者。 下列範例示範如何使用不同類型的翻轉並排顯示。  
  
### <a name="to-tile-an-image"></a>若要並排顯示影像  
  
-   此範例會使用下列的 75 × 75 映像，以並排顯示 200 × 200 的矩形。  
  
 ![圖格 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")  
  
-   下圖顯示矩形與影像如何並排顯示。 請注意，所有圖格都具有相同的方向;沒有開關。  
  
 ![圖格 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>若要翻轉並排顯示時的水平影像  
  
-   此範例會使用相同的 75 × 75 映像，以填滿 200 × 200 的矩形。 自動換行模式設定為水平翻轉影像。 下圖顯示矩形與影像如何並排顯示。 請注意，當從一個圖格移至指定的資料列中的下一步 時，會水平翻轉影像。  
  
 ![圖格 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>若要翻轉垂直在並排顯示時的映像  
  
-   此範例會使用相同的 75 × 75 映像，以填滿 200 × 200 的矩形。 自動換行模式設定為垂直翻轉影像。  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>若要在並排顯示時水平及垂直翻轉影像  
  
-   此範例會使用相同的 75 × 75 映像，以並排顯示 200 × 200 的矩形。 自動換行模式設定為以水平和垂直翻轉影像。 下圖顯示矩形的影像如何並排顯示。 請注意，您從一個圖格移至下一步 指定的資料列中，水平翻轉影像，並當從一個圖格移至指定的資料行中的下一步 時，要以垂直方式翻轉影像。  
  
 ![圖格 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>另請參閱
- [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
