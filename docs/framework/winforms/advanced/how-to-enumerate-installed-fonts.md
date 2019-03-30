---
title: HOW TO：列舉已安裝的字型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: e56f06d6f7a762a1ef1ff85fa30751ea64f9f14b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653739"
---
# <a name="how-to-enumerate-installed-fonts"></a>HOW TO：列舉已安裝的字型
<xref:System.Drawing.Text.InstalledFontCollection>類別繼承自<xref:System.Drawing.Text.FontCollection>抽象基底類別。 您可以使用<xref:System.Drawing.Text.InstalledFontCollection>物件來列舉電腦上安裝的字型。 <xref:System.Drawing.Text.FontCollection.Families%2A>的屬性<xref:System.Drawing.Text.InstalledFontCollection>物件為陣列的<xref:System.Drawing.FontFamily>物件。  
  
## <a name="example"></a>範例  
 下列範例會列出安裝在電腦上的所有字型家族的名稱。 程式碼會擷取<xref:System.Drawing.FontFamily.Name%2A>屬性的每個<xref:System.Drawing.FontFamily>中所傳回的陣列物件<xref:System.Drawing.Text.FontCollection.Families%2A>屬性。 系列名稱是擷取，串連這些區塊是以逗號分隔的格式清單。 然後<xref:System.Drawing.Graphics.DrawString%2A>方法的<xref:System.Drawing.Graphics>類別在矩形中繪製的逗號分隔清單。  
  
 如果您執行範例程式碼時，輸出會類似下圖所示：  
  
 ![如果螢幕擷取畫面會顯示已安裝的字型系列。](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例中專為搭配 Windows Form 使用，而且需要<xref:System.Windows.Forms.PaintEventArgs> `e`，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。 此外，您應該匯入<xref:System.Drawing.Text>命名空間。  
  
## <a name="see-also"></a>另請參閱
- [使用字型和文字](using-fonts-and-text.md)
