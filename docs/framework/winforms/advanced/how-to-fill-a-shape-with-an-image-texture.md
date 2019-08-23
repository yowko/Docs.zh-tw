---
title: HOW TO：使用影像材質填滿形狀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911681"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>作法：使用影像材質填滿形狀
您可以使用<xref:System.Drawing.Image>類別<xref:System.Drawing.TextureBrush>和類別, 以材質填滿封閉圖形。  
  
## <a name="example"></a>範例  
 下列範例會以影像填滿橢圓形。 程式<xref:System.Drawing.Image>代碼會建立物件, 然後將該<xref:System.Drawing.Image>物件的位址當做引數傳遞至<xref:System.Drawing.TextureBrush.%23ctor%2A>函式。 第三個語句會縮放影像, 而第四個語句會以重複的縮放影像複本來填滿橢圓形。  
  
 在下列程式碼中, <xref:System.Drawing.TextureBrush.Transform%2A>屬性包含在繪製之前套用至影像的轉換。 假設原始影像的寬度為640圖元, 而高度為480圖元。 轉換會藉由設定水準和垂直縮放值, 將影像縮小為75×75。  
  
> [!NOTE]
> 在下列範例中, 影像大小為75× 75, 而橢圓形大小為150×250。 因為影像小於所填滿的橢圓形, 所以橢圓形會與影像並排顯示。 並排表示影像會以水準和垂直方式重複, 直到達到圖形的邊界為止。 如需並排顯示的詳細資訊[, 請參閱如何:以影像](how-to-tile-a-shape-with-an-image.md)並排顯示圖形。  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是針對與 Windows Forms 搭配使用所設計, 而且它<xref:System.Windows.Forms.PaintEventArgs>需要`e`, 這<xref:System.Windows.Forms.Control.Paint>是事件處理常式的參數。  
  
## <a name="see-also"></a>另請參閱

- [使用筆刷填滿形狀](using-a-brush-to-fill-shapes.md)
