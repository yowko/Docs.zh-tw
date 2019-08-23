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
ms.openlocfilehash: 23d9374f1f46c4480079eb4ad5269a197a13a5bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963883"
---
# <a name="types-of-coordinate-systems"></a>座標系統類型
GDI + 使用三個座標空間: [世界]、[頁面] 和 [裝置]。 全局座標是用來建立特定圖形世界模型的座標, 而且是您傳遞給 .NET Framework 中方法的座標。 頁面座標指的是繪圖介面所使用的座標系統, 例如表單或控制項。 裝置座標是用來繪製實體裝置的座標, 例如, 螢幕或紙張紙。 當您進行`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`呼叫時, 您傳遞<xref:System.Drawing.Graphics.DrawLine%2A>給方法的點 (`(0, 0)`和`(160, 80)`) 會在全局座標空間中。 在 GDI + 可以繪製螢幕上的線條之前, 座標會傳遞一系列轉換。 一個轉換 (稱為「世界」轉換) 會將全局座標轉換成頁面座標, 另一個轉換 (稱為「頁面」轉換) 會將頁面座標轉換成裝置座標。  
  
## <a name="transforms-and-coordinate-systems"></a>轉換和座標系統  
 假設您想要使用座標系統, 其原點在工作區的主體中, 而不是左上角。 比方說, 假設您希望原點是100圖元, 從工作區的左邊緣, 到工作區頂端50圖元。 下圖顯示這類座標系統。  
  
 ![座標系統](./media/aboutgdip05-art01.gif "AboutGdip05_art01")  
  
 當您進行呼叫`myGraphics.DrawLine(myPen, 0, 0, 160, 80)`時, 您會看到下圖所示的那一行。  
  
 ![座標系統](./media/aboutgdip05-art02.gif "AboutGdip05_art02")  
  
 在三個座標空間中, 線條的端點座標如下所示:  
  
|||  
|-|-|  
|成為|(0, 0) 到 (160, 80)|  
|頁面|(100, 50) 到 (260, 130)|  
|裝置|(100, 50) 到 (260, 130)|  
  
 請注意, 頁面座標空間的原點在工作區的左上角;這一律會是這種情況。 另請注意, 因為測量單位是圖元, 所以裝置座標與頁面座標相同。 如果您將測量單位設定為圖元以外的值 (例如, 英寸), 則裝置座標會與頁面座標不同。  
  
 將全局座標對應至頁面座標的「世界」轉換會保留在<xref:System.Drawing.Graphics.Transform%2A> <xref:System.Drawing.Graphics>類別的屬性中。 在上述範例中, 世界轉換是 x 方向的轉譯100單位和 y 方向的50單位。 下列範例會設定<xref:System.Drawing.Graphics>物件的世界轉換, 然後使用該<xref:System.Drawing.Graphics>物件繪製如上圖所示的線條:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 頁面轉換會將頁面座標對應至裝置座標。 <xref:System.Drawing.Graphics>類別提供和<xref:System.Drawing.Graphics.PageScale%2A>屬性, 用於動作頁面轉換。 <xref:System.Drawing.Graphics.PageUnit%2A> 類別也提供兩個唯讀<xref:System.Drawing.Graphics.DpiX%2A>屬性和<xref:System.Drawing.Graphics.DpiY%2A>, 以檢查顯示裝置的每英寸水準和垂直點。 <xref:System.Drawing.Graphics>  
  
 您可以使用<xref:System.Drawing.Graphics.PageUnit%2A> <xref:System.Drawing.Graphics>類別的屬性來指定圖元以外的量值單位。  
  
> [!NOTE]
> 您無法將<xref:System.Drawing.Graphics.PageUnit%2A>屬性設定為<xref:System.Drawing.GraphicsUnit.World>, 因為這不是實體單位, 而且會造成例外狀況。  
  
 下列範例會繪製從 (0, 0) 到 (2, 1) 的線條, 其中的點 (2, 1) 從點到右, 1 英寸向下 (0, 0):  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> 如果您在建立畫筆時未指定畫筆寬度, 上述範例會繪製一條寬度為一英寸寬的線條。 您可以在函式的第二個引數<xref:System.Drawing.Pen>中指定畫筆寬度:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 假設顯示裝置的水準方向有96個點, 以及垂直方向的每英寸96個點, 則上述範例中的線條端點在三個座標空間中具有下列座標:  
  
|||  
|-|-|  
|成為|(0, 0) 到 (2, 1)|  
|頁面|(0, 0) 到 (2, 1)|  
|裝置|(0, 0, 至 (192, 96)|  
  
 請注意, 因為全局座標空間的原點是在工作區的左上角, 所以頁面座標與全局座標相同。  
  
 您可以結合世界和頁面轉換來達到各種效果。 例如, 假設您想要使用英寸做為測量單位, 而您想要座標系統的原點是2英寸, 從工作區的左邊緣到1/2 英寸, 從工作區的頂端開始。 下列範例會設定<xref:System.Drawing.Graphics>物件的世界和頁面轉換, 然後繪製從 (0, 0) 到 (2, 1) 的線條:  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 下圖顯示線條和座標系統。  
  
 ![座標系統](./media/aboutgdip05-art03.gif "AboutGdip05_art03")  
  
 假設顯示裝置的水準方向有96個點, 以及垂直方向的每英寸96個點, 則上述範例中的線條端點在三個座標空間中具有下列座標:  
  
|||  
|-|-|  
|成為|(0, 0) 到 (2, 1)|  
|頁面|(2, 0.5) 至 (4, 1.5)|  
|裝置|(192, 48) 到 (384, 144)|  
  
## <a name="see-also"></a>另請參閱

- [座標系統和轉換](coordinate-systems-and-transformations.md)
- [以矩陣來表示轉換](matrix-representation-of-transformations.md)
