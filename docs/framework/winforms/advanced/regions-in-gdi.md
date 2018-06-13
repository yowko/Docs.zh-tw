---
title: GDI+ 中的區域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: dc7f10571163d447802c90cd61d71b11d0e695d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524579"
---
# <a name="regions-in-gdi"></a>GDI+ 中的區域
區域是輸出裝置的顯示區域的一部分。 區域可以是簡單 （單一矩形） 或複雜 （多邊形和封閉型曲線的組合）。 下圖顯示兩個區域： 其中一個矩形中，從建構和路徑中的其他建構。  
  
 ![區域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>使用區域  
 通常用於裁剪區域，並點擊測試。 裁剪包括限制到特定區域的 [顯示] 區域中，通常需要更新的部分的繪圖。 點擊測試，包括檢查以判斷游標是否已為螢幕的某些區域中按下滑鼠按鈕時。  
  
 您可以建構從矩形或路徑的區域。 您也可以結合現有的區域，以建立複雜的區域。 <xref:System.Drawing.Region>類別會提供下列方法來結合區域： <xref:System.Drawing.Region.Intersect%2A>， <xref:System.Drawing.Region.Union%2A>， <xref:System.Drawing.Region.Xor%2A>， <xref:System.Drawing.Region.Exclude%2A>，和<xref:System.Drawing.Region.Complement%2A>。  
  
 兩個區域的交集是屬於這兩個區域的所有點的集合。 等位是屬於一或兩個區域的所有點的集合。 區域的補數是一組不在區域的所有點。 下圖顯示在上圖中顯示兩個區域的聯集和交集。  
  
 ![區域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A>地區、 一組套用的方法會產生包含隸屬於一個區域或其他的但非兩者的所有點的區域。 <xref:System.Drawing.Region.Exclude%2A>地區、 一組套用的方法會產生包含所有的第一個區域中的點不在第二個區域的區域。 下圖顯示將套用所得到的地區<xref:System.Drawing.Region.Xor%2A>和<xref:System.Drawing.Region.Exclude%2A>本主題開頭所顯示的兩個區域的方法。  
  
 ![區域](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 若要填滿區域時，您需要<xref:System.Drawing.Graphics>物件<xref:System.Drawing.Brush>物件，和<xref:System.Drawing.Region>物件。 <xref:System.Drawing.Graphics>物件提供<xref:System.Drawing.Graphics.FillRegion%2A>方法，而<xref:System.Drawing.Brush>物件儲存的填滿，例如色彩或圖樣的屬性。 下列範例會填滿包含純色的區域。  
  
 [!code-csharp[LinesCurvesAndShapes#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [線條、曲線和形狀](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [使用區域](../../../../docs/framework/winforms/advanced/using-regions.md)
