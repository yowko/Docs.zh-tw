---
title: 作法：使用複合模式控制 Alpha 透明混色
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 6863e59efa25323f80933bf8ab595316b430ef53
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590136"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>作法：使用複合模式控制 Alpha 透明混色
可能有您想来建立一個幕外的點陣圖，具有下列特性：  
  
- 色彩必須是小於 255 的 alpha 值。  
  
- 色彩不 alpha 混色彼此，當您在建立點陣圖。  
  
- 當您顯示完成的點陣圖時，點陣圖中的色彩會是 alpha 混色與顯示裝置上的背景色彩。  
  
 若要建立這種點陣圖，建構空白<xref:System.Drawing.Bitmap>物件，然後再建構<xref:System.Drawing.Graphics>物件會根據該點陣圖。 設定的複合 （compositing） 模式<xref:System.Drawing.Graphics>物件至<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>。  
  
## <a name="example"></a>範例  
 下列範例會建立<xref:System.Drawing.Graphics>物件根據<xref:System.Drawing.Bitmap>物件。 此程式碼使用<xref:System.Drawing.Graphics>物件以及兩個半透明筆刷 (alpha = 160) 來繪製點陣圖。 紅色的橢圓形和綠色橢圓形使用半透明筆刷，會填滿的程式碼。 綠色的橢圓形重疊紅色的省略符號，但因為綠色不會以紅色混合的複合 （compositing） 模式<xref:System.Drawing.Graphics>物件設定為<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>。  
  
 程式碼會繪製點陣圖在螢幕上兩次： 彩色背景上白色背景上一次，一次。 屬於兩個橢圓形的點陣圖中像素會有的 alpha 元件為 160，因此橢圓形會混合與在螢幕上的背景色彩。  
  
 下圖顯示程式碼範例的輸出。 請注意混合與背景，在省略符號，但它們不能彼此。  
  
 ![圖表顯示省略符號與背景，不互相混合。](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 在程式碼範例包含此陳述式：  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 如果您想要混合彼此以及與背景的省略符號，請將陳述式變更如下：  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 下圖顯示修改過的程式碼的輸出。  
  
 ![此圖顯示省略符號混合在一起，並具有背景。](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Color.FromArgb%2A>
- [Alpha 混色線條和填色](alpha-blending-lines-and-fills.md)
