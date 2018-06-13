---
title: 如何：建構字型系列和字型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: ceace5950ec135ea4d52081da7d1de7a820583ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520886"
---
# <a name="how-to-construct-font-families-and-fonts"></a>如何：建構字型系列和字型
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 字型的字體相同但不同的樣式分組字型家族。 例如，新細明體字型系列包含下列字型：  
  
-   新細明體一般  
  
-   新細明體粗體  
  
-   新細明體，斜體  
  
-   新細明體  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 使用四個以表單系列樣式： 一般、 粗體、 斜體和粗體斜體。 例如形容詞*縮小*和*四捨五入*不會被視為樣式; 而是它們是完整的系列名稱。 例如，新細明體窄是字型家族具有下列成員：  
  
-   新細明體窄的規則  
  
-   粗體的新細明體  
  
-   新細明體窄斜體  
  
-   窄的新細明體  
  
 您可以繪製的文字之前[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，您必須建構<xref:System.Drawing.FontFamily>物件和<xref:System.Drawing.Font>物件。 <xref:System.Drawing.FontFamily>物件指定字體 （例如，新細明體），而<xref:System.Drawing.Font>物件指定大小、 樣式和單位。  
  
## <a name="example"></a>範例  
 下列範例會建構標準大小為 16 個像素的新細明體字型樣式。 在下列程式碼中，第一個引數傳遞給<xref:System.Drawing.Font.%23ctor%2A>建構函式是<xref:System.Drawing.FontFamily>物件。 第二個引數會指定第四個引數所識別的單位之字型的大小。 第三個引數識別樣式。  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> 成員的<xref:System.Drawing.GraphicsUnit>列舉型別和<xref:System.Drawing.FontStyle.Regular>隸屬<xref:System.Drawing.FontStyle>列舉型別。  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計用於搭配 Windows Form，且其需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>另請參閱  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
