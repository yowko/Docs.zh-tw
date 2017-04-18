---
title: "預覽事件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "事件, 預覽"
  - "事件, 隱藏"
  - "預覽事件"
  - "隱藏事件"
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 預覽事件
預覽事件 \(也稱為通道事件\) 是一種路由事件，其路由方向是從應用程式根目錄，指向引發事件且事件資料中回報為來源的項目。  不是所有的事件案例都可支援或需要預覽事件；本主題說明有預覽事件存在的情況，應用程式或元件處理這種事件的方式，以及可能需要在自訂元件或類別中建立預覽事件的狀況。  
  
## 預覽事件和輸入  
 處理一般預覽事件時，如果要在事件資料中將事件標示為已處理，請務必小心。  在任何項目上處理預覽事件 \(但引發該事件，也就是在事件資料中回報為來源的項目除外\)，都會讓項目沒有機會處理其來源事件。  這有時候是預期的結果，尤其是相關項目與撰寫控制項有關時。  
  
 對於輸入事件，預覽事件也會特別與對應反昇事件共用事件資料執行個體。  如果您使用預覽事件類別處理常式將輸入事件標記為已處理，便不會叫用反昇輸入事件類別處理常式。  或者，如果您使用預覽事件執行個體常式將事件標記為已處理，通常也不會叫用反昇事件的處理常式。  即使事件已標記為已處理，類別處理常式或執行個體處理常式還是可以註冊或附加要叫用的選項，但是一般不建議您使用這種方法。  
  
 如需類別處理及其與預覽事件之關係的詳細資訊，請參閱[將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)。  
  
### 解決控制項隱藏的事件  
 經常使用預覽事件的其中一個案例是輸入事入的複合控制項處理。  有時候，控制項的作者會隱藏控制項產生的特定事件，目的可能是要替換成元件定義的事件，以提供更詳細的資訊或更具體的行為。  例如，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> 會隱藏 <xref:System.Windows.Controls.Button> 或其複合項目產生的 <xref:System.Windows.UIElement.MouseLeftButtonDown> 和 <xref:System.Windows.UIElement.MouseLeftButtonDown> 反昇事件，將其取代為擷取滑鼠以及引發 <xref:System.Windows.Controls.Button> 本身一定會引發的<xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  事件及其資料仍會循著路由傳送，但是因為 <xref:System.Windows.Controls.Button> 將事件標記為 <xref:System.Windows.RoutedEventArgs.Handled%2A>，所以只會叫用具體指出本身應該在 `handledEventsToo` 案例中作用的事件處理常式。  如果指向應用程式根目錄的其他項目仍然希望有機會處理控制項隱藏的事件，其中一種選擇是在程式碼中附加處理常式，並將 `handledEventsToo` 指定為 `true`。  但是通常比較簡單的做法是將您處理的路由目錄變更為輸入事件的預覽對等項目。  例如，如果控制項隱藏了 <xref:System.Windows.UIElement.MouseLeftButtonDown>，請嘗試改成附加 <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> 的處理常式。  這種方法只適用於基底項目輸入事件，例如 <xref:System.Windows.UIElement.MouseLeftButtonDown>。  這些輸入事件會使用通道\/反昇配對、引發兩種事件，並共用事件資料。  
  
 這些方法各有其副作用或限制。  處理預覽事件的副作用是在該時點處理事件可能會停用應該處理反昇事件的處理常式，因此其限制是當事件還在路由的預覽部分時，將它標記為已處理通常不是適當的做法。  `handledEventsToo` 方法的限制是您不能在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中指定 `handledEventsToo` 處理常式做為屬性 \(Attribute\)，而且必須在取得要附加處理常式之項目的物件參考之後，在程式碼中註冊事件處理常式。  
  
## 請參閱  
 [將路由事件標記為已處理以及類別處理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [路由事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)