---
title: HOW TO：使用單色填滿形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: d6fe7a252029ff80f21d99f7342fabb1d29fbe24
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211669"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a>HOW TO：使用單色填滿形狀
若要使用純色，填滿形狀，建立<xref:System.Drawing.SolidBrush>物件，然後再將它傳遞<xref:System.Drawing.SolidBrush>物件做為其中一個的 fill 方法的引數為<xref:System.Drawing.Graphics>類別。 下列範例示範如何使用紅色的色彩填滿橢圓形。  
  
## <a name="example"></a>範例  
 下列程式碼中，<xref:System.Drawing.SolidBrush.%23ctor%2A>建構函式接受<xref:System.Drawing.Color>物件做為其唯一引數。 使用的值<xref:System.Drawing.Color.FromArgb%2A>方法來表示色彩的 alpha、 紅色、 綠色和藍色元件。 每個這些值必須是 0 到 255 範圍內。 第 255 表示色彩是完全不透明的而且第二個 255 表示紅色元件的濃度。 兩個零表示綠色和藍色元件這兩個 0 的濃度。  
  
 四個數字 （0，0，100，60） 傳遞至<xref:System.Drawing.Graphics.FillEllipse%2A>方法指定的橢圓形的週框矩形的大小與位置。 矩形的左上角 （0，0），寬度為 100，而高度為 60。  
  
 [!code-csharp[System.Drawing.UsingABrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- [使用筆刷填滿形狀](using-a-brush-to-fill-shapes.md)
