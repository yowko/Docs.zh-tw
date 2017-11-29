---
title: "如何：繪製不透明和半透明線條"
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
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea65fd836a6e6fc00472f6139a0700ea859545cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>如何：繪製不透明和半透明線條
當您繪製一條線時，必須傳遞 <xref:System.Drawing.Pen> 物件至 <xref:System.Drawing.Graphics> 類別的 <xref:System.Drawing.Graphics.DrawLine%2A> 方法。 <xref:System.Drawing.Pen.%23ctor%2A> 建構函式的其中一個參數是 <xref:System.Drawing.Color> 物件。 若要繪製不透明的線條，請將色彩的 Alpha 元件設為 255。 若要繪製半透明線條，請將 Alpha 元件設為從 1 到 254 的任何值。  
  
 當您在背景上繪製半透明線條時，線條的色彩會與背景的色彩混合。 Alpha 元件指定如何混合線條和背景色彩；接近於 0 的 Alpha 值給予背景色彩較多的權重，而接近 255 的 Alpha 值給予線條色彩較多的權重。  
  
## <a name="example"></a>範例  
 下列範例會繪製點陣圖，然後繪製以該點陣圖做為背景的三條線。 第一條線使用的 Alpha 元件為 255，所以是不透明的。 第二和第三條線使用的 Alpha 元件為 128，因此是半透明的；您可以透過線條看到背景影像。 設定 <xref:System.Drawing.Graphics.CompositingQuality%2A> 屬性的陳述式會讓第三條線搭配 Gamma 修正進行混色。  
  
 下圖顯示下列程式碼的輸出。  
  
 ![不透明和半透明](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱  
 [Alpha 混色線條和填色](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [操作說明：為控制項提供透明背景](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [操作說明：使用不透明和半透明筆刷繪製](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
