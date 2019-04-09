---
title: HOW TO：將 Gamma 修正套用至漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: 7290b7901714e9b71bda3f85f930f5331b8fd4ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077325"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>HOW TO：將 Gamma 修正套用至漸層
您可以藉由設定筆刷的線性漸層筆刷的 gamma 修正<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>屬性設`true`。 您可以設定連線，停用 gamma 修正<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>屬性設`false`。 預設會停用 gamma 修正。  
  
## <a name="example"></a>範例  
 範例會建立線形漸層筆刷，並使用以填滿兩個矩形的筆刷。 Gamma 修正沒有填滿第一個矩形，第二個矩形填滿的 gamma 修正。  
  
 下圖顯示兩個填滿的矩形。 最上方的矩形，並沒有 gamma 修正，會在中間項目出現深。 下方的矩形，其具有 gamma 修正，似乎有多個統一的濃度。  
  
 ![漸層停駐](./media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.Control.Paint>事件處理常式。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Drawing2D.LinearGradientBrush>
- [使用漸層筆刷填滿形狀](using-a-gradient-brush-to-fill-shapes.md)
