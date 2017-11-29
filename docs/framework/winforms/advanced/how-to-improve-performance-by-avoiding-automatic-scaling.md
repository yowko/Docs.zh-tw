---
title: "如何：避免自動縮放以提高效能"
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
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0130e0745dfca20da5dc723bb7cc84748bb0b148
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>如何：避免自動縮放以提高效能
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可能會自動隨著映像您繪製，反而會降低效能。 或者，您可以控制傳遞到目的地矩形的維度影像的縮放<xref:System.Drawing.Graphics.DrawImage%2A>方法。  
  
 例如，下列呼叫<xref:System.Drawing.Graphics.DrawImage%2A>方法指定的左上角 （50，30），但未指定目的地矩形。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 雖然這是最簡單的版本<xref:System.Drawing.Graphics.DrawImage%2A>方法所需的引數數量不一定是最有效率。 如果解析由[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)](通常是 96 dpi) 不同於儲存在解析<xref:System.Drawing.Image>物件，則<xref:System.Drawing.Graphics.DrawImage%2A>方法將縮放影像。 例如，假設<xref:System.Drawing.Image>物件具有 216 像素為單位的寬度和水平解析度是預存的值為 72 dpi。 因為 216/72 為 3， <xref:System.Drawing.Graphics.DrawImage%2A> ，使其具有 3 英吋的寬度解析度為 96 dpi 縮放影像。 也就是說，<xref:System.Drawing.Graphics.DrawImage%2A>會顯示影像的寬度為 96 x 3 = 288，像素為單位。  
  
 即使您的螢幕解析度 96 dpi，從不同[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]將可能刻度影像好像螢幕解析度 96 dpi。 這是因為[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<xref:System.Drawing.Graphics>物件都與裝置內容，以及當[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]螢幕解析度時，結果的裝置內容通常是 96，不論實際螢幕解析度的查詢。 您可以藉由指定目的地矩形中的自動調整，避免<xref:System.Drawing.Graphics.DrawImage%2A>方法。  
  
## <a name="example"></a>範例  
 下列範例會繪製兩次相同的映像。 在第一個案例中，未指定目的地矩形的高度與寬度，並自動縮放影像。 在第二個案例中，寬度和目的地矩形的高度 （單位為像素為單位） 指定要做為原始影像的高度與寬度會相同。 下圖顯示兩次呈現的影像。  
  
 ![調整紋理](../../../../docs/framework/winforms/advanced/media/csscaledtexture1.png "csscaledtexture1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 取代 Texture.jpg 映像名稱和您系統為有效的路徑。  
  
## <a name="see-also"></a>另請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [使用影像、點陣圖、圖示和中繼檔](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
