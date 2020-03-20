---
title: 如何：使用文字反鋸齒功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182477"
---
# <a name="how-to-use-antialiasing-with-text"></a>如何：使用文字反鋸齒功能
*抗鋸齒*是指平滑繪製圖形和文本的鋸齒邊緣，以提高其外觀或可讀性。 使用託管 GDI+ 類，您可以呈現高品質的反鋸齒文本以及較低品質的文本。 通常，與較低品質的渲染相比，更高品質的渲染需要更多的處理時間。 要設置文本品質級別，將<xref:System.Drawing.Graphics.TextRenderingHint%2A>屬性<xref:System.Drawing.Graphics>設置為<xref:System.Drawing.Text.TextRenderingHint>枚舉的元素之一  
  
## <a name="example"></a>範例  
 以下代碼示例繪製具有兩種不同品質設置的文本。  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 下圖顯示了示例代碼的輸出：  
  
 ![顯示具有兩種不同品質設置的文本的螢幕截圖。](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 前面的代碼示例設計用於 Windows 表單，它要求<xref:System.Windows.Forms.PaintEventArgs>`e`. <xref:System.Windows.Forms.PaintEventHandler>  
  
## <a name="see-also"></a>另請參閱

- [使用字型和文字](using-fonts-and-text.md)
