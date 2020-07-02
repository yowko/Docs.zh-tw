---
title: 如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動
description: 瞭解如何使用 Windows Forms 的雙重緩衝來減少圖形閃爍，並使用控制項來解決與繪製作業相關聯的閃爍問題。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618125"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>如何：使用表單和控制項的雙重緩衝以減少圖形重繪閃動
雙重緩衝會使用記憶體緩衝區來解決多個與繪製作業建立關聯的閃爍問題。 啟用雙重緩衝時，會將所有繪製作業都轉譯到記憶體緩衝區，而不是螢幕上的繪圖介面。 在所有繪製作業都完成之後，會直接將記憶體緩衝區複製到與其建立關聯的繪圖介面。 因為只有一個圖形作業會在螢幕上執行，所以會消除與複雜繪製作業相關聯的影像閃爍。對於大部分的應用程式而言，.NET Framework 所提供的預設雙重緩衝會提供最佳的結果。 預設會將標準 Windows Forms 控制項進行雙重緩衝處理。 您可以透過兩種方式在表單和撰寫的控制項中啟用預設雙重緩衝。 您可以將屬性設定 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 為 `true` ，也可以呼叫方法，將 <xref:System.Windows.Forms.Control.SetStyle%2A> 旗標設定 <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> 為 `true` 。 這兩種方法都會啟用表單或控制項的預設雙重緩衝，並提供無閃爍的圖形呈現。 <xref:System.Windows.Forms.Control.SetStyle%2A>只有您已撰寫所有呈現程式碼的自訂控制項，才建議呼叫方法。  
  
 如需更先進的雙重緩衝案例，例如動畫或先進的記憶體管理，您可以執行自己的雙重緩衝邏輯。 如需詳細資訊，請參閱[如何：手動管理已緩衝的圖形](how-to-manually-manage-buffered-graphics.md)。  
  
### <a name="to-reduce-flicker"></a>減少閃爍  
  
- 將 <xref:System.Windows.Forms.Control.DoubleBuffered%2A> 屬性設為 `true`。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- 或 -  
  
- 呼叫 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法，將旗標設定 <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> 為 `true` 。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [雙重緩衝的圖形](double-buffered-graphics.md)
- [Windows Form 中的圖形和繪圖](graphics-and-drawing-in-windows-forms.md)
