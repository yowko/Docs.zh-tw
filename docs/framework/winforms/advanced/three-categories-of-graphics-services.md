---
title: 圖形服務的三個分類
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: fa7391ef0f7170ddb9d9d24aa5a1a03635bf46e0
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291731"
---
# <a name="three-categories-of-graphics-services"></a>圖形服務的三個分類
Windows 表單中的圖形產品分為以下三大類：  
  
- 二維 （二-D） 向量圖形  
  
- 建立映像  
  
- 印刷樣式  
  
## <a name="2d-vector-graphics"></a>2D 向量圖形  
 二維向量圖形（如直線、曲線和圖形）是由坐標系上的點集指定的基元。 例如，直線由其兩個端點指定，矩形由一個點指定，該點給出其左上角的位置，以及一對表示其寬度和高度的數位。 簡單路徑由由直線連接的點陣列指定。 貝塞爾樣條線是由四個控制點指定的複雜曲線。  
  
 GDI+ 提供類和結構，這些類和結構存儲有關基元本身的資訊、存儲有關基元繪製方式的資訊的類以及實際執行繪圖的類。 例如，結構存儲<xref:System.Drawing.Rectangle>矩形的位置和大小;例如，該結構存儲矩形的位置和大小。類<xref:System.Drawing.Pen>存儲有關線顏色、線寬和線樣式的資訊;<xref:System.Drawing.Graphics>類具有繪製線條、矩形、路徑和其他圖形的方法。 還有幾個<xref:System.Drawing.Brush>類存儲有關如何用顏色或圖案填充閉合的數位和路徑的資訊。  
  
 您可以在中繼檔中記錄向量圖像（即圖形命令序列）。 GDI+ 提供<xref:System.Drawing.Imaging.Metafile>用於錄製、顯示和保存中繼檔的類。 使用<xref:System.Drawing.Imaging.MetafileHeader>和<xref:System.Drawing.Imaging.MetaHeader>類，可以檢查存儲在中繼檔標頭中的資料。  
  
## <a name="imaging"></a>建立映像  
 使用向量圖形技術很難或不可能顯示某些類型的圖片。 例如，工具列按鈕上的圖片和顯示為圖示的圖片很難指定為線條和曲線的集合。 使用向量技術，製作擁擠的棒球場的高解析度數位照片就更加困難了。 此類型的圖像存儲為點陣圖，即表示螢幕上單個點顏色的數位陣列。 GDI+ 提供<xref:System.Drawing.Bitmap>用於顯示、操作和保存點陣圖的類。  
  
## <a name="typography"></a>印刷樣式  
 排版是文本以各種字體、大小和樣式顯示的。 GDI+ 為這一複雜任務提供了廣泛的支援。 GDI+ 中的新功能之一是子圖元抗鋸齒，它使在 LCD 螢幕上呈現的文本外觀更平滑。  
  
 此外，Windows 表單還提供使用類<xref:System.Windows.Forms.TextRenderer>中的 GDI 功能繪製文本的選項。  
  
## <a name="see-also"></a>另請參閱

- [圖形概觀](graphics-overview-windows-forms.md)
- [關於 GDI+ Managed 程式碼](about-gdi-managed-code.md)
- [使用 Managed 圖形類別](using-managed-graphics-classes.md)
