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
ms.openlocfilehash: 33d4f4ecca7b9d777fa4eab5b6d031de10f03ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956784"
---
# <a name="regions-in-gdi"></a>GDI+ 中的區域
區域是輸出裝置的顯示區域的一部分。 區域可以是簡單 （一個矩形） 或複雜 （多邊形和封閉型曲線的組合）。 下圖顯示兩個區域： 其中一個矩形，從建構和其他建構從路徑。  
  
 ![Regions](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>使用區域  
 通常用於裁剪區域，和點擊測試。 裁剪是指限制到特定區域的顯示區域，通常需要更新的部分繪圖。 點擊測試，包括檢查並判斷游標是否在特定區域的畫面在按下滑鼠按鈕時。  
  
 您可以建構從矩形或路徑的區域。 您也可以藉由結合現有的區域建立複雜的區域。 <xref:System.Drawing.Region>類別提供下列方法來結合區域： <xref:System.Drawing.Region.Intersect%2A>， <xref:System.Drawing.Region.Union%2A>， <xref:System.Drawing.Region.Xor%2A>， <xref:System.Drawing.Region.Exclude%2A>，和<xref:System.Drawing.Region.Complement%2A>。  
  
 兩個區域的交集是屬於這兩個區域的所有點的集合。 聯集是一組屬於其中一個或兩個區域的所有點。 區域的補數是一組不在區域中的所有點。 下圖顯示在上圖中顯示的兩個區域的聯集和交集。  
  
 ![Regions](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A>方法，套用至配對的區域，會產生包含隸屬於一個區域或其他的但非兩者的所有點的區域。 <xref:System.Drawing.Region.Exclude%2A>方法，套用至配對的區域，會產生包含中的第一個區域不在第二個區域中的所有點的區域。 下圖顯示將套用所得到的區域<xref:System.Drawing.Region.Xor%2A>和<xref:System.Drawing.Region.Exclude%2A>方法來顯示位於本主題開頭的兩個區域。  
  
 ![Regions](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 若要填滿的區域，您需要<xref:System.Drawing.Graphics>物件，<xref:System.Drawing.Brush>物件，和<xref:System.Drawing.Region>物件。 <xref:System.Drawing.Graphics>物件會提供<xref:System.Drawing.Graphics.FillRegion%2A>方法，而<xref:System.Drawing.Brush>物件會儲存屬性的 fill 設定，例如色彩或圖樣。 下列範例會填滿區域，以使用純色。  
  
 [!code-csharp[LinesCurvesAndShapes#61](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [線條、曲線和形狀](lines-curves-and-shapes.md)
- [使用區域](using-regions.md)
