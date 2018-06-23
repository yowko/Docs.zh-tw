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
ms.openlocfilehash: 2adb33e3d05e38ee71be8a12cdc2e20dc8c55c72
ms.sourcegitcommit: ceca5a1c027627abcca2767567703c3879f33325
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2018
ms.locfileid: "36338126"
---
# <a name="how-to-use-antialiasing-with-text"></a>如何：使用文字反鋸齒功能
*消除鋸齒*指的是繪製的圖形和文字，以提高其外觀或可讀性的鋸齒邊緣平滑化。 使用 managed[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]類別，您可以轉譯高品質的反鋸齒文字，以及較低的品質文字。 通常，較高品質的呈現方式只需要處理時間會比低品質的呈現方式。 若要設定的文字品質等級，設定<xref:System.Drawing.Graphics.TextRenderingHint%2A>屬性<xref:System.Drawing.Graphics>其中一個項目的<xref:System.Drawing.Text.TextRenderingHint>列舉  
  
## <a name="example"></a>範例  
 下列程式碼範例會繪製具有兩個不同的品質設定的文字。  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 下圖顯示的範例程式碼的輸出：  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述程式碼範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
