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
ms.openlocfilehash: d157b51e24009d847dede9ea6a9f81c8898c5b06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-fonts-and-text"></a>使用字型和文字
所提供的許多類別[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]Windows Form 上繪製文字。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics>類別有數個<xref:System.Drawing.Graphics.DrawString%2A>方法可讓您指定的文字，例如位置、 週框矩形、 字型及格式的各種功能。 此外，您可以在 繪圖，並測量的文字[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]使用靜態<xref:System.Windows.Forms.TextRenderer.DrawText%2A>和<xref:System.Windows.Forms.TextRenderer.MeasureText%2A>方法所提供`TextRenderer`類別。 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]方法也可讓您指定的位置、 字型及格式。 您可以任選[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]或[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]文字轉譯; 不過，[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]通常提供較佳的效能和更精確測量的文字。 用於文字轉譯的其他類別包含`FontFamily`， `Font`， <xref:System.Drawing.StringFormat>，和`TextFormatFlags`。  
  
## <a name="in-this-section"></a>本節內容  
 [操作說明：建構字型系列和字型](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 示範如何建立`Font`和`FontFamily`物件。  
  
 [操作說明：在指定的位置繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 描述如何繪製文字中特定位置使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。  
  
 [操作說明：在矩形中繪製被包圍的文字](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 說明如何繪製矩形，利用文字[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]。  
  
 [操作說明：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 示範如何使用[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]來繪製文字。  
  
 [操作說明：對齊繪製的文字](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 示範如何格式化[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]和[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]文字。  
  
 [操作說明：建立垂直文字](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 描述如何繪製垂直對齊的文字與[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。  
  
 [操作說明：在已繪製的文字中設定定位停駐點](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 顯示如何繪製文字的定位停駐點[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。  
  
 [操作說明：列舉已安裝的字型](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 說明如何列出已安裝的字型名稱。  
  
 [操作說明：建立私用字型集合](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 描述如何建立<xref:System.Drawing.Text.PrivateFontCollection>物件。  
  
 [操作說明：取得字型度量資訊](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 示範如何取得字型度量資訊，例如方格上移和下移。  
  
 [操作說明：使用文字反鋸齒功能](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 說明如何使用時繪製文字的消除鋸齒。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Drawing.Font>  
 描述這個類別，並包含其所有成員的連結。  
  
 <xref:System.Drawing.FontFamily>  
 描述這個類別，並包含其所有成員的連結。  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 描述這個類別，並包含其所有成員的連結。  
  
 <xref:System.Windows.Forms.TextRenderer>  
 描述這個類別，並包含其所有成員的連結。  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 描述這個類別，並包含其所有成員的連結。
