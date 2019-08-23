---
title: 作法：在繪製的文字中設定定位停駐點
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947825"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>作法：在繪製的文字中設定定位停駐點
您可以藉<xref:System.Drawing.StringFormat.SetTabStops%2A>由呼叫<xref:System.Drawing.StringFormat>物件的方法, 然後將該<xref:System.Drawing.StringFormat>物件<xref:System.Drawing.Graphics.DrawString%2A>傳遞至<xref:System.Drawing.Graphics>類別的方法, 來為文字設定 tab 鍵停止。  
  
> [!NOTE]
> 雖然您可以<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>使用旗標來展開現有的定位停駐點, 但不支援將定位點加入至繪製的文字。 <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>  
  
## <a name="example"></a>範例  
 下列範例會在150、250和350中設定制表位。 然後, 程式碼會顯示名稱和測試分數的索引標籤式清單。  
  
 下圖顯示索引標籤式文字:  
  
 ![顯示名稱和分數索引標籤式清單的螢幕擷取畫面。](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 下列程式碼會將兩個自<xref:System.Drawing.StringFormat.SetTabStops%2A>變數傳遞給方法。 第二個引數是包含定位字元位移的陣列。 傳遞至<xref:System.Drawing.StringFormat.SetTabStops%2A>的第一個引數為 0, 表示陣列中的第一個位移是從位置 0 (周框的左邊緣) 來測量。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
- 上述範例是針對與 Windows Forms 搭配使用所設計, 而且它<xref:System.Windows.Forms.PaintEventArgs>需要`e`, <xref:System.Windows.Forms.PaintEventHandler>這是的參數。  
  
## <a name="see-also"></a>另請參閱

- [使用字型和文字](using-fonts-and-text.md)
- [如何：使用 GDI 繪製文字](how-to-draw-text-with-gdi.md)
