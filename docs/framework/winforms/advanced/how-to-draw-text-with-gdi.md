---
title: "如何：使用 GDI 繪製文字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6c7fb4d8c6bd93481935a9f2ef7dd4b34af7e71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-with-gdi"></a>如何：使用 GDI 繪製文字
與<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法中的<xref:System.Windows.Forms.TextRenderer>類別，您可以存取[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]表單或控制項上繪製文字的功能。 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]文字轉譯通常提供較佳的效能和更精確的文字比測量[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法<xref:System.Windows.Forms.TextRenderer>類別不支援列印。 列印時，一律使用<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用矩形內的多行上繪製文字<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法。  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 與文字呈現<xref:System.Windows.Forms.TextRenderer>類別，您需要<xref:System.Drawing.IDeviceContext>，例如<xref:System.Drawing.Graphics>和<xref:System.Drawing.Font>，來繪製文字，並在其中它應該繪製的色彩的位置。 您可以選擇性地指定文字格式使用<xref:System.Windows.Forms.TextFormatFlags>列舉型別。  
  
 如需有關取得<xref:System.Drawing.Graphics>，請參閱[How to： 建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。 如需有關建構<xref:System.Drawing.Font>，請參閱[How to： 建構字型系列和字型](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述程式碼範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
