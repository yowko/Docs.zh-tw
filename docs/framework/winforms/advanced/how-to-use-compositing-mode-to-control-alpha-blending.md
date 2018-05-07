---
title: 如何：使用複合模式控制 Alpha 混色
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 55c6db1029c6823652ac29fca46f6f8dc4ec40d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>如何：使用複合模式控制 Alpha 混色
有時可能會當您想要建立螢幕的點陣圖，具有下列特性：  
  
-   色彩的 alpha 值小於 255。  
  
-   色彩不 alpha 彼此混合，當您建立的點陣圖。  
  
-   當您顯示完成的點陣圖時，點陣圖中的色彩是 alpha 混色與顯示裝置上的背景色彩。  
  
 若要建立這類點陣圖，建構空白<xref:System.Drawing.Bitmap>物件，然後再建構<xref:System.Drawing.Graphics>物件會根據該點陣圖。 設定複合模式的<xref:System.Drawing.Graphics>物件<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>。  
  
## <a name="example"></a>範例  
 下列範例會建立<xref:System.Drawing.Graphics>物件根據<xref:System.Drawing.Bitmap>物件。 程式碼會使用<xref:System.Drawing.Graphics>以及兩個半透明筆刷的物件 (alpha = 160) 來繪製在點陣圖。 程式碼會填入紅色橢圓形和綠色橢圓形使用半透明筆刷。 綠色橢圓形重疊紅色的省略符號，但因為綠色不會以紅色混合的複合模式<xref:System.Drawing.Graphics>物件設定為<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>。  
  
 程式碼繪製點陣圖螢幕上兩次： 彩色的背景上白色背景上一次，一次。 屬於兩個橢圓形的像素點陣圖中擁有的 alpha 元件為 160，因此橢圓形會與在螢幕上的背景色彩混合。  
  
 下圖顯示程式碼範例的輸出。 請注意，省略符號會混合背景，但它們不能與彼此。  
  
 ![來源複製](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")  
  
 程式碼範例包含此陳述式：  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 如果您想要混合彼此以及與背景的省略符號，變更該陳述式所示：  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 下圖顯示已修訂的程式碼的輸出。  
  
 ![來源透過](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [Alpha 混色線條和填色](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
