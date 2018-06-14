---
title: 如何：在已繪製的文字中設定定位停駐點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: e7f3fe9757db26bcc9dc9735f3d3d854edb7c099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523633"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>如何：在已繪製的文字中設定定位停駐點
您可以藉由呼叫設定定位停駐點的文字<xref:System.Drawing.StringFormat.SetTabStops%2A>方法<xref:System.Drawing.StringFormat>物件，然後再傳遞<xref:System.Drawing.StringFormat>物件<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>無法支援新增定位停駐點繪製的文字中，雖然您可以擴充現有的索引標籤可讓您停止使用<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>旗標。  
  
## <a name="example"></a>範例  
 下列範例會在 150、 250 和 350 設定定位停駐點。 然後，程式碼會顯示索引標籤式的名字和分數測試清單。  
  
 下圖顯示索引標籤式的文字。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")  
  
 下列程式碼會傳遞兩個引數<xref:System.Drawing.StringFormat.SetTabStops%2A>方法。 第二個引數是陣列，其中包含的索引標籤的位移。 第一個引數傳遞至<xref:System.Drawing.StringFormat.SetTabStops%2A>為 0，表示陣列中的第一個位移，從位置 0，這個周框左邊緣算起。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## <a name="see-also"></a>另請參閱  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [操作說明：使用 GDI 繪製文字](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
