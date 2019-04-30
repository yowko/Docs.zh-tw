---
title: HOW TO：使用 CompositionTarget 在單格間隔進行轉譯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 00b416d423a4bdc8bab576add2d77fd305ea6e0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008924"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>HOW TO：使用 CompositionTarget 在單格間隔進行轉譯
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎提供許多建立畫面型動畫的功能。 不過，有些應用程式案例需要依據每個畫面進行更細微的控制。 <xref:System.Windows.Media.CompositionTarget>物件讓您能夠建立自訂動畫，根據每個畫面的回呼。  
  
 <xref:System.Windows.Media.CompositionTarget> 是靜態類別，它代表繪製您的應用程式在顯示介面。 <xref:System.Windows.Media.CompositionTarget.Rendering>繪製應用程式的場景每次引發事件。 轉譯畫面播放速率是每秒繪製場景的次數。  
  
> [!NOTE]
>  使用完整的程式碼範例<xref:System.Windows.Media.CompositionTarget>，請參閱 <<c2> [ 使用 CompositionTarget 範例](https://go.microsoft.com/fwlink/?LinkID=160045)。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.CompositionTarget.Rendering>期間就會引發事件[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]轉譯程序。 下列範例示範如何註冊<xref:System.EventHandler>委派給靜態<xref:System.Windows.Media.CompositionTarget.Rendering>方法<xref:System.Windows.Media.CompositionTarget>。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 您可以使用轉譯事件處理常式方法來建立自訂的繪製內容。 系統會針對每個畫面呼叫一次此事件處理常式方法。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 每次封送處理視覺化樹狀結構中已保存的轉譯資料，跨越到組合場景圖形時，就會呼叫您的事件處理常式方法。 此外，如果視覺化樹狀結構的變更強迫更新組合場景圖形，也會呼叫您的事件處理常式方法。 請注意，計算版面配置之後會呼叫您的事件處理常式方法。 不過，您可以在您的事件處理常式方法中修改版面配置，這表示轉譯之前會再次計算版面配置。  
  
 下列範例示範如何提供自訂繪製<xref:System.Windows.Media.CompositionTarget>事件處理常式方法。 在此案例中的背景色彩<xref:System.Windows.Controls.Canvas>繪製滑鼠座標位置為基礎的色彩值。 如果您移動滑鼠<xref:System.Windows.Controls.Canvas>、 其背景色彩變更。 此外，也會根據目前的已耗用時間和已轉譯畫面的總數目，計算平均畫面播放速率。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 您可能會發現您的自訂繪製在不同電腦上的執行速度不同。 因為自訂繪製並非獨立於畫面撥放速率。 根據您所執行的系統和該系統的工作負載<xref:System.Windows.Media.CompositionTarget.Rendering>不同數目的每秒的時間可能會呼叫事件。 如需判斷執行 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式之裝置的圖形硬體功能及效能的詳細資訊，請參閱[圖形轉譯層](../advanced/graphics-rendering-tiers.md)。  
  
 新增或移除轉譯<xref:System.EventHandler>時引發事件的委派會延遲到完成的事件之後引發。 這是的方式一致<xref:System.MulticastDelegate>-Common Language Runtime (CLR) 會處理基礎的事件。 另請注意，不保證會以特定的順序呼叫轉譯事件。 如果您有多個<xref:System.EventHandler>委派依賴特定順序，您應該登錄單一<xref:System.Windows.Media.CompositionTarget.Rendering>事件並進行多工處理中正確的委派排列自己。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.CompositionTarget>
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
