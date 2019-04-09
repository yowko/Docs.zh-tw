---
title: HOW TO：建構字型家族和字型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: 0a9dcd00d4bc3e64ae4fc9a1d4884fac18521825
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181216"
---
# <a name="how-to-construct-font-families-and-fonts"></a>HOW TO：建構字型家族和字型
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 分組的字型系列字樣相同但不同的字型。 比方說，新細明體字型系列包含下列字型：  
  
-   新細明體的一般  
  
-   新細明體粗體  
  
-   新細明體斜體  
  
-   新細明體  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 使用表單系列的四個樣式： 一般、 粗體、 斜體和粗體斜體。 這類的形容詞*縮小*並*捨入*不會被視為樣式; 而是它們屬於的系列名稱。 比方說，新細明體窄時，為字型家族，具有下列成員：  
  
-   新細明體窄一般  
  
-   粗體的新細明體  
  
-   新細明體窄斜體  
  
-   窄的新細明體  
  
 您可以繪製的文字之前[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您必須建構<xref:System.Drawing.FontFamily>物件和<xref:System.Drawing.Font>物件。 <xref:System.Drawing.FontFamily>物件會指定 （例如，新細明體），字樣和<xref:System.Drawing.Font>物件指定大小、 樣式和單位。  
  
## <a name="example"></a>範例  
 下列範例會建構規則的樣式新細明體字型的大小為 16 個像素。 在下列程式碼中，第一個引數傳遞給<xref:System.Drawing.Font.%23ctor%2A>建構函式是<xref:System.Drawing.FontFamily>物件。 第二個引數會指定在第四個引數所識別的單位中測量的字型的大小。 第三個引數識別的樣式。  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> 隸屬<xref:System.Drawing.GraphicsUnit>列舉型別，並<xref:System.Drawing.FontStyle.Regular>隸屬<xref:System.Drawing.FontStyle>列舉型別。  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs>`e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱

- [使用字型和文字](using-fonts-and-text.md)
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
