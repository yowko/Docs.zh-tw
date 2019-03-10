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
ms.openlocfilehash: c9fe16752223203806c7d3828f632aad0cab0c28
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703360"
---
# <a name="using-fonts-and-text"></a>使用字型和文字
所提供的許多類別[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]Windows Form 上繪製文字。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics>類別有數個<xref:System.Drawing.Graphics.DrawString%2A>方法，可讓您指定的文字，例如地點、 週框矩形、 字型和格式的各種功能。 此外，您可以在其中繪製並測量的文字[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]使用靜態<xref:System.Windows.Forms.TextRenderer.DrawText%2A>並<xref:System.Windows.Forms.TextRenderer.MeasureText%2A>方法所提供`TextRenderer`類別。 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]方法也可讓您指定的位置、 字型和格式。 您可以選擇[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]或是[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]的文字呈現; 不過，[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]通常提供較佳的效能和更精確測量的文字。 用於文字轉譯的其他類別包含`FontFamily`， `Font`， <xref:System.Drawing.StringFormat>，和`TextFormatFlags`。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建構字型系列和字型](how-to-construct-font-families-and-fonts.md)  
 示範如何建立`Font`和`FontFamily`物件。  
  
 [如何：在指定的位置繪製文字](how-to-draw-text-at-a-specified-location.md)  
 描述如何繪製在特定位置中使用的文字[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。  
  
 [如何：在矩形中繪製被包圍的文字](how-to-draw-wrapped-text-in-a-rectangle.md)  
 說明如何繪製在矩形中使用的文字[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。  
  
 [如何：使用 GDI 繪製文字](how-to-draw-text-with-gdi.md)  
 示範如何使用[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]繪製文字。  
  
 [如何：對齊繪製的文字](how-to-align-drawn-text.md)  
 示範如何格式化[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]文字。  
  
 [如何：建立垂直文字](how-to-create-vertical-text.md)  
 描述如何繪製垂直對齊的文字與[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。  
  
 [如何：在繪製文字中設定定位停駐點](how-to-set-tab-stops-in-drawn-text.md)  
 示範如何使用繪製文字與定位停駐點[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。  
  
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
