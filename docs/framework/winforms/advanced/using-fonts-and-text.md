---
title: 使用字型和文字
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505116"
---
# <a name="using-fonts-and-text"></a>使用字型和文字
有數個 Windows Form 上繪製文字的 GDI + 和 GDI 所提供的類別。 GDI +<xref:System.Drawing.Graphics>類別有數個<xref:System.Drawing.Graphics.DrawString%2A>方法，可讓您指定的文字，例如地點、 週框矩形、 字型和格式的各種功能。 此外，您可以在其中繪製並測量的文字與使用靜態的 GDI<xref:System.Windows.Forms.TextRenderer.DrawText%2A>並<xref:System.Windows.Forms.TextRenderer.MeasureText%2A>所提供的方法`TextRenderer`類別。 GDI 方法也可讓您指定的位置、 字型和格式。 您可以選擇 GDI 或 GDI + 的文字呈現;不過，GDI 通常提供較佳的效能和更精確測量的文字。 用於文字轉譯的其他類別包含`FontFamily`， `Font`， <xref:System.Drawing.StringFormat>，和`TextFormatFlags`。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建構字型系列和字型](how-to-construct-font-families-and-fonts.md)  
 示範如何建立`Font`和`FontFamily`物件。  
  
 [如何：在指定的位置繪製文字](how-to-draw-text-at-a-specified-location.md)  
 描述如何在特定位置使用 GDI + 和 GDI 繪製文字。  
  
 [如何：在矩形中繪製被包圍的文字](how-to-draw-wrapped-text-in-a-rectangle.md)  
 說明如何使用 GDI + 和 GDI 矩形中繪製文字。  
  
 [如何：使用 GDI 繪製文字](how-to-draw-text-with-gdi.md)  
 示範如何使用 GDI 繪製文字。  
  
 [如何：對齊繪製的文字](how-to-align-drawn-text.md)  
 示範如何設定 GDI + 和 GDI 文字格式。  
  
 [如何：建立垂直文字](how-to-create-vertical-text.md)  
 描述如何繪製使用 GDI + 的垂直對齊的文字。  
  
 [如何：在繪製文字中設定定位停駐點](how-to-set-tab-stops-in-drawn-text.md)  
 示範如何使用繪製文字使用 GDI + 的定位停駐點。  
  
 [如何：列舉已安裝的字型](how-to-enumerate-installed-fonts.md)  
 說明如何列出已安裝的字型的名稱。  
  
 [如何：建立私用字型集合](how-to-create-a-private-font-collection.md)  
 描述如何建立<xref:System.Drawing.Text.PrivateFontCollection>物件。  
  
 [如何：取得字型度量資訊](how-to-obtain-font-metrics.md)  
 示範如何取得字型度量資訊，例如方格上移和下移。  
  
 [如何：使用文字反鋸齒功能](how-to-use-antialiasing-with-text.md)  
 說明如何繪製文字時使用消除鋸齒。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Drawing.Font>  
 描述這個類別，並且包含其所有成員的連結。  
  
 <xref:System.Drawing.FontFamily>  
 描述這個類別，並且包含其所有成員的連結。  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 描述這個類別，並且包含其所有成員的連結。  
  
 <xref:System.Windows.Forms.TextRenderer>  
 描述這個類別，並且包含其所有成員的連結。  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 描述這個類別，並且包含其所有成員的連結。
