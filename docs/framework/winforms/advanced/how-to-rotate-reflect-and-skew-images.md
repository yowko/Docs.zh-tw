---
title: HOW TO：旋轉、 反射和傾斜影像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 3e539f41667edb505269fe420396c79b68f34e8f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711495"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>HOW TO：旋轉、 反射和傾斜影像
您可以旋轉、 反射和傾斜影像藉由指定之左上角、 右上方和左下角邊角原始映像的目的點。 這三個目的點決定仿射轉換，原始的矩形映像會對應至平行四邊形。  
  
## <a name="example"></a>範例  
 例如，假設原始的映像會在左上角的矩形 （0，0），在右上角 （100，0），並在左下角 （0，50）。 現在假設您將這些對應三個點至目的地點，如下所示。  
  
|原始的點|目的地點|  
|--------------------|-----------------------|  
|左上角 （0，0）|(200, 20)|  
|右上方 （100，0）|(110, 100)|  
|左下角 （0，50）|(250, 30)|  
  
 下圖顯示原始的映像和對應的平行四邊形的映像。 原始的映像具有已扭曲、 反映、 旋轉和轉譯。 原始的映像的上邊緣的 x 軸會對應到執行的那一行 （200，20） 和 （110，100）。 原始的映像的左邊緣沿著 y 軸會對應到執行的那一行 （200，20） 和 250 (30）。  
  
 ![等量分散](./media/stripes1.gif "Stripes1")  
  
 下圖類似的轉換套用至相片的映像。  
  
 ![轉換的 Climber](./media/transformedclimber.png "TransformedClimber")  
  
 下圖類似的轉換套用至中繼檔。  
  
 ![轉換中繼檔](./media/transformedmetafile.png "TransformedMetafile")  
  
 下列範例會產生的第一個圖例中顯示的映像。  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例是為了搭配 Windows Form 使用而設計，且其需要 <xref:System.Windows.Forms.PaintEventArgs>`e`，這是 <xref:System.Windows.Forms.Control.Paint> 事件處理常式的參數。 請務必取代`Stripes.bmp`適用於您的系統映像的路徑。  
  
## <a name="see-also"></a>另請參閱
- [使用影像、點陣圖、圖示和中繼檔](working-with-images-bitmaps-icons-and-metafiles.md)
