---
title: HOW TO：使用文字消除鋸齒功能
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
ms.openlocfilehash: 080d946bd72da8b76ed846efdf149eb328d66336
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505724"
---
# <a name="how-to-use-antialiasing-with-text"></a>作法：使用文字消除鋸齒功能
*消除鋸齒*指的繪製的圖形和文字，以提高它們的外觀或可讀性的鋸齒狀邊緣變得平滑。 您可以使用 managed GDI + 類別，來呈現高品質的反鋸齒文字，以及較低的品質文字。 一般而言，較高品質的呈現方式會比較低品質的更多處理時間。 若要設定文字的品質層級，設定<xref:System.Drawing.Graphics.TextRenderingHint%2A>的屬性<xref:System.Drawing.Graphics>其中一個項目的<xref:System.Drawing.Text.TextRenderingHint>列舉  
  
## <a name="example"></a>範例  
 下列程式碼範例會繪製兩個不同的品質設定的文字。  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 下圖顯示的範例程式碼的輸出：  
  
 ![如果螢幕擷取畫面顯示兩個不同的品質設定的文字。](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述程式碼範例專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱

- [使用字型和文字](using-fonts-and-text.md)
