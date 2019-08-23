---
title: 作法：使用 CompositionTarget 在單格間隔進行轉譯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 8864204ccdd1e860cc910dfe8baa2f25edfb2fcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956988"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>作法：使用 CompositionTarget 在單格間隔進行轉譯
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎提供許多建立畫面型動畫的功能。 不過，有些應用程式案例需要依據每個畫面進行更細微的控制。 <xref:System.Windows.Media.CompositionTarget>物件可以根據每個畫面格回呼來建立自訂動畫。  
  
 <xref:System.Windows.Media.CompositionTarget>是靜態類別, 代表您的應用程式繪製所在的顯示介面。 每<xref:System.Windows.Media.CompositionTarget.Rendering>次繪製應用程式的場景時, 就會引發事件。 轉譯畫面播放速率是每秒繪製場景的次數。  
  
> [!NOTE]
> 如需使用<xref:System.Windows.Media.CompositionTarget>的完整程式碼範例, 請參閱[使用 CompositionTarget 範例](https://go.microsoft.com/fwlink/?LinkID=160045)。  
  
## <a name="example"></a>範例  
 事件會在轉譯過程[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中引發。 <xref:System.Windows.Media.CompositionTarget.Rendering> 下列範例顯示如何在上<xref:System.EventHandler> <xref:System.Windows.Media.CompositionTarget>註冊靜態<xref:System.Windows.Media.CompositionTarget.Rendering>方法的委派。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 您可以使用轉譯事件處理常式方法來建立自訂的繪製內容。 系統會針對每個畫面呼叫一次此事件處理常式方法。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 每次封送處理視覺化樹狀結構中已保存的轉譯資料，跨越到組合場景圖形時，就會呼叫您的事件處理常式方法。 此外，如果視覺化樹狀結構的變更強迫更新組合場景圖形，也會呼叫您的事件處理常式方法。 請注意，計算版面配置之後會呼叫您的事件處理常式方法。 不過，您可以在您的事件處理常式方法中修改版面配置，這表示轉譯之前會再次計算版面配置。  
  
 下列範例會示範如何在<xref:System.Windows.Media.CompositionTarget>事件處理常式方法中提供自訂繪圖。 在此情況下, 的背景色彩<xref:System.Windows.Controls.Canvas>會根據滑鼠的座標位置繪製色彩值。 如果您將滑鼠移到內部<xref:System.Windows.Controls.Canvas>, 其背景色彩就會變更。 此外，也會根據目前的已耗用時間和已轉譯畫面的總數目，計算平均畫面播放速率。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 您可能會發現您的自訂繪製在不同電腦上的執行速度不同。 因為自訂繪製並非獨立於畫面撥放速率。 視您正在執行的系統和該系統的工作負載而定, <xref:System.Windows.Media.CompositionTarget.Rendering>每秒可能會呼叫事件數個不同的次數。 如需判斷執行 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式之裝置的圖形硬體功能及效能的詳細資訊，請參閱[圖形轉譯層](../advanced/graphics-rendering-tiers.md)。  
  
 在事件引發時加入<xref:System.EventHandler>或移除轉譯委派, 將會延遲到事件完成引發為止。 這與 Common Language Runtime <xref:System.MulticastDelegate>(CLR) 中處理事件的方式一致。 另請注意，不保證會以特定的順序呼叫轉譯事件。 如果您有多<xref:System.EventHandler>個依賴特定順序的委派, 您應該註冊單一<xref:System.Windows.Media.CompositionTarget.Rendering>事件, 並自行以正確的順序來進行委派。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Media.CompositionTarget>
- [WPF 圖形轉譯概觀](wpf-graphics-rendering-overview.md)
