---
title: "使用字型和文字 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "範例 [Windows Form], 字型和文字"
  - "字型, 在 Windows Form 中使用"
  - "GDI, 描繪文字 [Windows Form]"
  - "字串 [Windows Form], 在 Windows Form 中描繪"
  - "文字 [Windows Form], 在 Windows Form 中描繪"
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 使用字型和文字
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 和 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 提供幾種在 Windows Form 上繪製文字的類別。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> 類別有幾種 <xref:System.Drawing.Graphics.DrawString%2A> 方法可以讓您指定各種文字功能，例如位置、週框 \(Bounding Rectangle\)、字型和格式。  此外，您也可以搭配 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 使用 `TextRenderer` 類別提供的靜態 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 和 <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> 方法，以繪製和測量文字。  [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 方法也可以讓您指定位置、字型和格式。  您可以選擇 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 或 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 呈現文字。然而，[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 通常會提供更好的效能以及更精確的文字測量。  其他組成文字呈現的類別包括 `FontFamily`、`Font`、<xref:System.Drawing.StringFormat> 和 `TextFormatFlags`。  
  
## 在本節中  
 [如何：建構字型系列和字型](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 示範如何建立 `Font` 和 `FontFamily` 物件。  
  
 [如何：在指定的位置繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 描述如何使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 和 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 在某些位置繪製文字。  
  
 [如何：在矩形中繪製被包圍的文字](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 解釋如何使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 和 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 在矩形中繪製文字。  
  
 [如何：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 示範如何使用 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 繪製文字。  
  
 [如何：對齊繪製的文字](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 示範如何格式化 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 和 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 文字。  
  
 [如何：建立垂直文字](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 說明如何使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 描繪垂直對齊的文字。  
  
 [如何：在已繪製的文字中設定定位停駐點](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 示範如何搭配定位停駐點使用 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 繪製文字。  
  
 [如何：列舉已安裝的字型](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 說明如何列出已安裝字型的名稱。  
  
 [如何：建立私用字型集合](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 示範如何建立 <xref:System.Drawing.Text.PrivateFontCollection> 物件。  
  
 [如何：取得字型度量資訊](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 示範如何取得字型度量資訊，例如儲存格高度和深度。  
  
 [如何：使用文字反鋸齒功能](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 說明在繪製文字時如何使用反鋸齒功能。  
  
## 參考  
 <xref:System.Drawing.Font>  
 不僅描述這個類別，並且提供連至它所有成員的連結。  
  
 <xref:System.Drawing.FontFamily>  
 不僅描述這個類別，並且提供連至它所有成員的連結。  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 不僅描述這個類別，並且提供連至它所有成員的連結。  
  
 <xref:System.Windows.Forms.TextRenderer>  
 不僅描述這個類別，並且提供連至它所有成員的連結。  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 不僅描述這個類別，並且提供連至它所有成員的連結。