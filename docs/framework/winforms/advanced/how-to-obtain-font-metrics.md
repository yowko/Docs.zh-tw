---
title: "如何：取得字型度量資訊"
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
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16f1126cc75b75ae98298f5d1c58c78ff30edbb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-font-metrics"></a>如何：取得字型度量資訊
<xref:System.Drawing.FontFamily>類別提供下列方法，擷取特定的系列樣式組合的各種度量：  
  
-   <xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)  
  
-   <xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)  
  
 這些方法所傳回的數字是單位為字型設計單位，因此它們都是獨立的大小和單位特定的<xref:System.Drawing.Font>物件。  
  
 下圖顯示各種標準。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")  
  
## <a name="example"></a>範例  
 下列範例會顯示標準的樣式，新細明體字型家族的度量。 程式碼也建立<xref:System.Drawing.Font>具有 16 個像素大小和顯示該特定的度量 （以像素為單位） （根據新細明體系列） 的物件<xref:System.Drawing.Font>物件。  
  
 下圖顯示的範例程式碼的輸出。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")  
  
 請注意上圖中的前兩行。 <xref:System.Drawing.Font>物件傳回的大小為 16，而<xref:System.Drawing.FontFamily>物件傳回 2048 em 高度。 這些兩個數字 （16 和 2048） 是用於轉換字型設計單位之間的單位 （在此案例的像素） 的關鍵<xref:System.Drawing.Font>物件。  
  
 例如，您可以將轉換 （堆疊） 設計單位為像素為單位，如下所示：  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")  
  
 下列程式碼文字垂直定位藉由設定<xref:System.Drawing.PointF.Y%2A>資料成員<xref:System.Drawing.PointF>物件。 Y 座標會增加`font.Height`每一個新的文字行。 <xref:System.Drawing.Font.Height%2A>屬性<xref:System.Drawing.Font>物件傳回該特定的行距 （單位為像素為單位）<xref:System.Drawing.Font>物件。 在此範例中，數字傳回<xref:System.Drawing.Font.Height%2A>為 19。 請注意，這是取得行距度量資訊轉換為像素 （無條件進位到整數） 的數字相同。  
  
 請注意，（也稱為大小或 em 大小） 其 em 高度不 （堆疊） 和深度的總和。 （堆疊） 和深度的總和稱為儲存格的高度。 儲存格的高度減去內部的前置字元會等於其 em 高度。 儲存格的高度加上外部的前置字元等於行距。  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
