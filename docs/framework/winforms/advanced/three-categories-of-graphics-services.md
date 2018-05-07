---
title: 圖形服務的三個分類
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: 5621a2c0bba2e922e62006feba9ca0381181c780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="three-categories-of-graphics-services"></a>圖形服務的三個分類
在 Windows Form 中的圖形供應項目可分為下列三個主要類別：  
  
-   二維 (2d) 向量圖形  
  
-   映像  
  
-   印刷樣式  
  
## <a name="2-d-vector-graphics"></a>2d 向量圖形  
 2d 向量圖形是基本型別。例如線條、 曲線和數字。所指定的座標系統上的點集合。 比方說，直線由兩個端點，並提供其左上角和提供其寬度和高度的數字組的位置點所指定的矩形。 連接的直線的點陣列所指定簡單的路徑。 貝茲曲線是由四個控點的高性能的曲線。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供類別和儲存自己的基本類型的相關資訊的結構、 類別可儲存資訊有關如何將繪製基本項目，以及實際進行繪製的類別。 比方說，<xref:System.Drawing.Rectangle>結構會儲存的位置和大小的矩形;<xref:System.Drawing.Pen>類別會儲存有關線條色彩、 線條寬度和線條樣式，而<xref:System.Drawing.Graphics>類別具有繪製線條、 矩形、 路徑、 方法和其他幾張圖。 有數個也<xref:System.Drawing.Brush>儲存方式的相關資訊的類別關閉圖表，而且路徑會填滿色彩或圖樣。  
  
 您可以記錄是一串圖形命令，以向量映像中繼檔中。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供<xref:System.Drawing.Imaging.Metafile>錄製、 顯示和儲存中繼檔的類別。 與<xref:System.Drawing.Imaging.MetafileHeader>和<xref:System.Drawing.Imaging.MetaHeader>類別，您可以檢查儲存在中繼檔標頭中的資料。  
  
## <a name="imaging"></a>映像  
 某些類型的圖片會很難或無法與向量圖形的技術一起顯示。 比方說，在工具列按鈕上的圖片，會顯示為圖示的圖片難以指定做為集合的直線和曲線。 高解析度數位擁擠的棒球場上所拍攝的相片是更難以建立與向量技巧。 此類型的影像會儲存為點陣圖，也就是數字，代表在螢幕上的每個點的色彩的陣列。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供<xref:System.Drawing.Bitmap>以便顯示、 管理，以及將點陣圖另存的類別。  
  
## <a name="typography"></a>印刷樣式  
 印刷樣式是文字的各種不同的字型、 大小及樣式中顯示。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 這個複雜的工作，提供更詳盡的支援。 中的新功能的其中一個[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]素反鋸齒功能，可讓文字呈現 LCD 螢幕更順暢的外觀。  
  
 此外，Windows Form 提供繪製文字的選項[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]中的功能及其<xref:System.Windows.Forms.TextRenderer>類別。  
  
## <a name="see-also"></a>另請參閱  
 [圖形概觀](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [關於 GDI+ Managed 程式碼](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [使用 Managed 圖形類別](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
