---
title: "如何：使用影像並排顯示圖案"
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
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f825371d3849e96ace627e660fd7c59bd290185
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-tile-a-shape-with-an-image"></a>如何：使用影像並排顯示圖案
磚可以放在相鄰涵蓋樓層，如同可以相鄰放置矩形的映像，填滿 （磚） 圖形。 若要並排顯示圖案的內部，使用紋理筆刷。 當您建構<xref:System.Drawing.TextureBrush>物件，其中您傳遞給建構函式的引數為<xref:System.Drawing.Image>物件。 當您使用的材質筆刷繪製圖形內部時，此映像的重複複本填滿的圖案。  
  
 自動換行模式屬性的<xref:System.Drawing.TextureBrush>物件決定如何將映像導向矩形格線中重複時。 您可以進行所有的磚，在方格中有相同的方向，或您可以進行映像從一個格線位置翻轉到下一步。 翻轉可以水平、 垂直或兩者。 下列範例示範使用不同的開關來並排顯示。  
  
### <a name="to-tile-an-image"></a>若要並排顯示影像  
  
-   這個範例會使用下列 75 × 75 映像來並排顯示 200 × 200 的矩形。  
  
 ![菾拏 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")  
  
-   下圖顯示如何與影像並排顯示矩形。 請注意，所有圖格都具有相同的方向。沒有任何翻轉。  
  
 ![磚 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a>若要翻轉並排顯示時的水平影像  
  
-   這個範例會使用相同 75 × 75 影像以填滿 200 × 200 的矩形。 換行模式設定為水平翻轉影像。 下圖顯示如何與影像並排顯示矩形。 請注意，當您從一個磚移至給定的資料列在下一步，水平翻轉影像。  
  
 ![磚 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a>若要翻轉垂直在並排顯示時的映像  
  
-   這個範例會使用相同 75 × 75 影像以填滿 200 × 200 的矩形。 換行模式設定為垂直翻轉影像。  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a>若要在並排顯示時水平及垂直翻轉影像  
  
-   這個範例會使用相同的 75 × 75 映像來並排顯示 200 × 200 的矩形。 換行模式設定為水平及垂直翻轉影像。 下圖顯示矩形影像如何並排顯示。 請注意，當您從一個磚移動到給定的資料列中的下一個水平翻轉影像，當您從一個磚移動到給定的資料行中的下，垂直翻轉影像。  
  
 ![磚 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>另請參閱  
 [使用筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
