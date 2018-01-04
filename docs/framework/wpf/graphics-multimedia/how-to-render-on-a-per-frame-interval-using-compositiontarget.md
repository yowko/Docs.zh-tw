---
title: "操作說明：使用 CompositionTarget 在單格間隔轉譯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb7e917c59f11ed78f8d44fa4b674d8d572f3623
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>操作說明：使用 CompositionTarget 在單格間隔轉譯
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 動畫引擎提供許多建立畫面型動畫的功能。 不過，有些應用程式案例需要依據每個畫面進行更細微的控制。 <xref:System.Windows.Media.CompositionTarget>物件可讓您建立自訂個別畫面格回呼為基礎的動畫。  
  
 <xref:System.Windows.Media.CompositionTarget>是代表繪製您的應用程式的顯示介面的靜態類別。 <xref:System.Windows.Media.CompositionTarget.Rendering>應用程式的場景會繪製每次引發事件。 轉譯畫面播放速率是每秒繪製場景的次數。  
  
> [!NOTE]
>  完整的程式碼範例使用<xref:System.Windows.Media.CompositionTarget>，請參閱[使用 CompositionTarget 範例](http://go.microsoft.com/fwlink/?LinkID=160045)。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.Media.CompositionTarget.Rendering>事件引發時[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]轉譯程序。 下列範例顯示如何註冊<xref:System.EventHandler>委派給靜態<xref:System.Windows.Media.CompositionTarget.Rendering>方法<xref:System.Windows.Media.CompositionTarget>。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 您可以使用轉譯事件處理常式方法來建立自訂的繪製內容。 系統會針對每個畫面呼叫一次此事件處理常式方法。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 每次封送處理視覺化樹狀結構中已保存的轉譯資料，跨越到組合場景圖形時，就會呼叫您的事件處理常式方法。 此外，如果視覺化樹狀結構的變更強迫更新組合場景圖形，也會呼叫您的事件處理常式方法。 請注意，計算版面配置之後會呼叫您的事件處理常式方法。 不過，您可以在您的事件處理常式方法中修改版面配置，這表示轉譯之前會再次計算版面配置。  
  
 下列範例示範如何提供自訂繪圖<xref:System.Windows.Media.CompositionTarget>事件處理常式方法。 在此情況下的背景色彩<xref:System.Windows.Controls.Canvas>繪製滑鼠座標位置為基礎的色彩值。 如果您移動滑鼠內<xref:System.Windows.Controls.Canvas>、 其背景色彩變更。 此外，也會根據目前的已耗用時間和已轉譯畫面的總數目，計算平均畫面播放速率。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 您可能會發現您的自訂繪製在不同電腦上的執行速度不同。 因為自訂繪製並非獨立於畫面撥放速率。 根據您所執行的系統和工作負載的系統，<xref:System.Windows.Media.CompositionTarget.Rendering>不同數目的每秒的時間可能會呼叫事件。 如需判斷執行 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式之裝置的圖形硬體功能及效能的詳細資訊，請參閱[圖形轉譯層](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)。  
  
 新增或移除轉譯<xref:System.EventHandler>時引發事件的委派會延遲到事件完成後引發。 這是的方式一致<xref:System.MulticastDelegate>-已處理 Common Language Runtime (CLR) 型的事件。 另請注意，不保證會以特定的順序呼叫轉譯事件。 如果您有多個<xref:System.EventHandler>委派依賴以特定順序，您應該註冊單一<xref:System.Windows.Media.CompositionTarget.Rendering>事件和多工處理的委派中的正確順序自己。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.CompositionTarget>  
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
