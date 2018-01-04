---
title: "如何：列舉已安裝的字型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 905b5ecbda58d2f7edb7fc30d5505eec63a64c2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-installed-fonts"></a>如何：列舉已安裝的字型
<xref:System.Drawing.Text.InstalledFontCollection>類別繼承自<xref:System.Drawing.Text.FontCollection>抽象基底類別。 您可以使用<xref:System.Drawing.Text.InstalledFontCollection>物件來列舉電腦上安裝的字型。 <xref:System.Drawing.Text.FontCollection.Families%2A>屬性<xref:System.Drawing.Text.InstalledFontCollection>物件是陣列<xref:System.Drawing.FontFamily>物件。  
  
## <a name="example"></a>範例  
 下列範例會列出電腦上安裝的所有字型家族的名稱。 程式碼會擷取<xref:System.Drawing.FontFamily.Name%2A>每個屬性<xref:System.Drawing.FontFamily>所傳回陣列中的物件<xref:System.Drawing.Text.FontCollection.Families%2A>屬性。 擷取系列名稱，如串連這些區塊是以逗號分隔的格式清單。 然後在<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別在矩形中繪製的逗號分隔清單。  
  
 如果您執行範例程式碼時，輸出會類似於下圖所示。  
  
 ![安裝字型](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。 此外，您應該匯入<xref:System.Drawing.Text>命名空間。  
  
## <a name="see-also"></a>請參閱  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
