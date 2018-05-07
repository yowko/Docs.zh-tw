---
title: 如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: 6e11e364af5dc361a24cdd88d72432d6ba4d4058
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動
雙重緩衝會使用記憶體緩衝區來解決多個與繪製作業建立關聯的閃爍問題。 啟用雙重緩衝時，會將所有繪製作業都轉譯到記憶體緩衝區，而不是螢幕上的繪圖介面。 在所有繪製作業都完成之後，會直接將記憶體緩衝區複製到與其建立關聯的繪圖介面。 因為只有一個圖形作業在螢幕上執行，所以複雜繪製作業相關聯的影像閃爍會被刪除。對於大部分的應用程式，預設雙重緩衝提供[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]會提供最佳的結果。 標準的 Windows Form 控制項是雙重緩衝的預設值。 您可以啟用雙重緩衝在表單中的預設值，並撰寫兩種方式的控制項。 您可以設定<xref:System.Windows.Forms.Control.DoubleBuffered%2A>屬性`true`，或您可以呼叫<xref:System.Windows.Forms.Control.SetStyle%2A>方法，以設定<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>旗標設為`true`。 這兩種方法將會啟用預設的雙重緩衝您的表單或控制項，並提供閃爍的圖形轉譯。 呼叫<xref:System.Windows.Forms.Control.SetStyle%2A>方法建議只用於已寫入所有的轉譯程式碼的自訂控制項。  
  
 更進階的雙重緩衝狀況，例如動畫或進階的記憶體管理，您可以實作您自己的雙重緩衝邏輯。 如需詳細資訊，請參閱[How to： 手動管理已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)。  
  
### <a name="to-reduce-flicker"></a>若要減少重繪閃動  
  
-   將 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 屬性設定為 `true`。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \-或-  
  
-   呼叫<xref:System.Windows.Forms.Control.SetStyle%2A>方法，以設定<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>旗標設為`true`。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [雙重緩衝的圖形](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [Windows Forms 中的圖形和繪圖](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
