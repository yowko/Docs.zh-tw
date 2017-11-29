---
title: "預覽事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 04bdf32ea329ff25fd62255b4512d8a9d5703b8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="preview-events"></a>預覽事件
預覽事件，也就是通道事件，是路由的事件，其中的路由方向是從應用程式根目錄，向引發事件，且會回報為事件資料來源的項目。 並非所有事件案例支援或需要預覽事件。本主題描述的情況下，其中預覽事件存在，應用程式或元件應如何處理它們和情況下，建立自訂元件或類別中預覽事件可能會適當。  
  
## <a name="preview-events-and-input"></a>預覽事件和輸入  
 當您處理的事件一般情況下，謹慎的預覽將事件標示事件中處理資料。 處理預覽事件的任何項目以外引發它 （報告為事件資料來源項目） 的項目有不提供項目有機會處理它所引發之事件的效果。 有時候這是預期的結果，尤其是有問題的項目存在於撰寫控制項中的關聯性。  
  
 輸入事件具體而言，預覽事件事件資料執行個體與共用對應反昇事件。 如果您使用預覽事件的類別處理常式來處理輸入的事件標記，反昇輸入的事件的類別處理常式不會叫用。 或者，如果您使用預覽事件的執行個體處理常式處理事件標記，反昇事件的處理常式不通常會叫用。 可以註冊類別處理常式或執行個體處理常式，或連接到要叫用即使事件標示為已處理，但該技術不常使用的選項。  
  
 如需類別處理，以及它與預覽事件詳細資訊，請參閱[標示路由傳送事件中當做 Handled，和類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)。  
  
### <a name="working-around-event-suppression-by-controls"></a>處理控制項的事件隱藏項目  
 通常用預覽事件的一個案例是複合控制項的輸入事件的處理。 有時候，控制項的作者隱藏特定事件來自從其控制項，或許是為了替換元件定義的事件，以提供更多的資訊或更具體的行為。 比方說， [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>隱藏<xref:System.Windows.UIElement.MouseLeftButtonDown>和<xref:System.Windows.UIElement.MouseLeftButtonDown>所引發的事件反昇<xref:System.Windows.Controls.Button>或複合項目以利於捕捉滑鼠和引發<xref:System.Windows.Controls.Primitives.ButtonBase.Click>一定所引發的事件<xref:System.Windows.Controls.Button>本身。 事件及其資料仍繼續此路由上，但因為<xref:System.Windows.Controls.Button>標記事件資料做為<xref:System.Windows.RoutedEventArgs.Handled%2A>，特別指出應扮演之事件的處理常式`handledEventsToo`案例會叫用。  如果朝向您的應用程式根目錄的其他項目仍然希望有機會處理控制隱藏的事件，一種替代方法是附加的程式碼中的處理常式`handledEventsToo`指定為`true`。 但通常較簡單的技術是要變更您要預覽相當於輸入事件的控制代碼的路由方向。 比方說，如果會隱藏控制項<xref:System.Windows.UIElement.MouseLeftButtonDown>，嘗試附加的處理常式<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>改為。 這項技術僅適用於基底項目輸入事件這類<xref:System.Windows.UIElement.MouseLeftButtonDown>。 這些輸入的事件使用通道/泡泡組、 引發兩個事件，且共用的事件資料。  
  
 每個這些技術有副作用或限制。 處理預覽事件的副作用是此時處理的事件可能會停用處理反昇事件中，預期的處理常式，因此限制是，它通常不建議您將事件處理仍在 Previ 時標記路由的新增部分。 限制`handledEventsToo`技巧是，您不能指定`handledEventsToo`中的處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]做為屬性，您必須註冊事件處理常式程式碼中取得要附加的處理常式的所在的物件參考的項目之後。  
  
## <a name="see-also"></a>另請參閱  
 [將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
