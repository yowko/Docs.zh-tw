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
ms.openlocfilehash: f7aa4de8a0d646c441d0921fb2561ef5a9480f4e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711214"
---
# <a name="three-categories-of-graphics-services"></a>圖形服務的三個分類
在 Windows Form 中的圖形供應項目可分為下列三個廣泛的類別：  
  
-   二維 (2-d) 向量圖形  
  
-   映像  
  
-   印刷樣式  
  
## <a name="2-d-vector-graphics"></a>2d 向量圖形  
 二維向量圖形是基本型別;例如線條、 曲線和圖形;由組點座標系統上所指定。 比方說，一條直線由其兩個端點，並讓其左上角，以及提供其寬度和高度的數字的一組的位置點所指定的矩形。 連接的直線，線條的點陣列所指定簡單的路徑。 貝茲曲線是由四個控制點的複雜的曲線。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供類別和儲存的基本項目本身的相關資訊的結構，用以儲存資訊有關如何將繪製基本項目和實際進行繪製的類別。 比方說，<xref:System.Drawing.Rectangle>結構會儲存的位置和大小的矩形<xref:System.Drawing.Pen>類別會儲存有關線條色彩、 線條寬度和線條樣式，和<xref:System.Drawing.Graphics>類別有方法來繪製線條、 矩形、 路徑和其他數字。 有數個也<xref:System.Drawing.Brush>儲存方式的相關資訊的類別會關閉數字，而且路徑會填滿色彩或圖樣。  
  
 您可以記錄向量映像，也就是一連串的圖形命令，在中繼檔中。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供<xref:System.Drawing.Imaging.Metafile>記錄、 顯示及儲存的中繼檔的類別。 具有<xref:System.Drawing.Imaging.MetafileHeader>和<xref:System.Drawing.Imaging.MetaHeader>類別，您可以檢查儲存在中繼檔標頭中的資料。  
  
## <a name="imaging"></a>映像  
 某些類型的圖片會很難或無法以顯示與向量圖形的技術。 比方說，在工具列按鈕上的圖片，會顯示為圖示的圖片很難進行指定為直線和曲線的集合。 太過擁擠的棒球最高解析度數位相片是更難以建立與向量技巧。 此類型的映像會儲存為點陣圖，也就是數字，代表在螢幕上的每個點的色彩的陣列。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供<xref:System.Drawing.Bitmap>以便顯示、 管理，以及將點陣圖儲存的類別。  
  
## <a name="typography"></a>印刷樣式  
 印刷樣式是文字的以各種不同的字型、 大小和樣式的顯示。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可廣泛支援這項複雜工作。 其中一項新功能[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]子像素反鋸齒功能，提供文字轉譯 LCD 螢幕較平滑的外觀。  
  
 此外，Windows Forms 會提供選項來繪製的文字[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]中的功能及其<xref:System.Windows.Forms.TextRenderer>類別。  
  
## <a name="see-also"></a>另請參閱
- [圖形概觀](graphics-overview-windows-forms.md)
- [關於 GDI+ Managed 程式碼](about-gdi-managed-code.md)
- [使用 Managed 圖形類別](using-managed-graphics-classes.md)
