---
title: 如何：將 Gamma 修正套用至漸層
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: 9c3c9c5c63194b1dee8314a1ef96497a8b78b5ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520730"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>如何：將 Gamma 修正套用至漸層
您可以藉由設定筆刷的啟用線性漸層筆刷的 gamma 修正<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>屬性`true`。 您可以藉由設定停用 gamma 修正<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>屬性`false`。 預設為停用 gamma 修正。  
  
## <a name="example"></a>範例  
 範例會建立線形漸層筆刷，並使用該筆刷填滿兩個矩形。 Gamma 修正沒有填滿第一個矩形，第二個矩形會填入 gamma 修正。  
  
 下圖顯示兩個填滿的矩形。 最上層的矩形中，並沒有 gamma 修正顯示暗色，中間。 下方的矩形，gamma 修正，其看似具有濃度較為一致。  
  
 ![漸層停駐](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [使用漸層筆刷填滿形狀](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
