---
title: "筆墨執行緒模型 | Microsoft Docs"
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
  - "應用程式使用介面執行緒"
  - "動態呈現執行緒"
  - "筆墨收集外掛程式"
  - "筆墨執行緒模型"
  - "筆墨, 呈現"
  - "畫筆執行緒"
  - "外掛程式, 適用於筆墨"
  - "呈現筆墨"
  - "手寫筆外掛程式"
  - "執行緒模型"
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 筆墨執行緒模型
Tablet PC 筆墨功能的其中一個優點，就是感覺很像用一般的筆和紙張寫字。  為了達到這種效果，Tablet 畫筆收集輸入資料的速度比滑鼠快得多，在使用者寫字時就能立即呈現筆墨。  應用程式的使用者介面 \(UI\) 執行緒不足以收集畫筆資料及呈現筆墨，因為會它可能會被封鎖。  為了解決這個問題，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式在使用者寫入筆墨時會使用兩個其他的執行緒。  
  
 下列清單說明收集和呈現數位筆墨時所使用的執行緒：  
  
-   畫筆執行緒：接收手寫筆輸入的執行緒  \(實際上，這是執行緒集區，但本主題中將此稱為畫筆執行緒\)。  
  
-   應用程式使用者介面執行緒：控制應用程式之使用者介面的執行緒。  
  
-   動態呈現執行緒：當使用者繪製筆劃時用於呈現筆墨的執行緒。  動態呈現執行緒不同於呈現應用程式中其他 UI 項目的執行緒，請參閱 Window Presentation Foundation [執行緒模型](../../../../docs/framework/wpf/advanced/threading-model.md)中的詳細說明。  
  
 不論應用程式使用的是 <xref:System.Windows.Controls.InkCanvas> 或是類似[建立筆墨輸入控制項](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)中的自訂控制項，筆墨模式都是一樣的。  雖然本主題是從 <xref:System.Windows.Controls.InkCanvas> 的觀點來討論執行緒，但是當您建立自訂控制項時仍適用相同的概念。  
  
## 執行緒概觀  
 下圖說明當使用者繪製筆劃時的執行緒模型：  
  
 ![繪製筆觸期間的執行緒模型。](../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading\_DrawingInk")  
  
1.  使用者繪製筆劃時發生的動作  
  
    1.  當使用者繪製筆劃時，手寫筆的點會進入畫筆執行緒中。  手寫筆外掛程式 \(包括 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>\) 會接受畫筆執行緒上手寫筆的點，並在 <xref:System.Windows.Controls.InkCanvas> 接收前先修改這些點。  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會在動態呈現執行緒上呈現手寫筆的點。  這個動作和上一個步驟是同時發生的。  
  
    3.  <xref:System.Windows.Controls.InkCanvas> 會接收 UI 執行緒上手寫筆的點。  
  
2.  使用者結束筆劃時發生的動作  
  
    1.  當使用者完成繪製筆劃時，<xref:System.Windows.Controls.InkCanvas> 會建立一個 <xref:System.Windows.Ink.Stroke> 物件並將物件加入至 <xref:System.Windows.Controls.InkPresenter> 以靜態呈現這個物件。  
  
    2.  UI 執行緒會提醒 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 已靜態呈現筆劃，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 就會移除筆劃的視覺化呈現。  
  
## 筆墨收集和手寫筆外掛程式  
 每一個 <xref:System.Windows.UIElement> 都有一個 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 中的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 物件會接收並修改畫筆執行緒上手寫筆的點。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 物件會按照在 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 中的順序接收手寫筆的點。  
  
 下圖的情況假設 <xref:System.Windows.UIElement> 的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合中，依序內含 `stylusPlugin1`、<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 及 `stylusPlugin2`。  
  
 ![StylusPlugin 效果輸出的順序。](../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading\_PluginOrder")  
  
 在上一個圖中會發生下列行為：  
  
1.  `StylusPlugin1` 會修改 x 和 y 的值。  
  
2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會接收修改過的手寫筆點，並呈現在動態呈現執行緒上。  
  
3.  `StylusPlugin2` 會接收修改過的手寫筆點，並進一步修改 x 和 y 的值。  
  
4.  應用程式會收集手寫筆的點，當使用者完成筆劃時，會靜態的呈現筆劃。  
  
 假設 `stylusPlugin1` 將手寫筆的點限制在矩形中，`stylusPlugin2` 則會將手寫筆的點轉譯到右邊。  在上一個情形中，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會接收被限制的手寫筆點，但不會接收轉譯後的手寫筆點。  當使用者繪製筆劃時，筆劃會呈現在矩形的界限內，但直到使用者提開畫筆時才會顯示轉譯後的筆劃。  
  
### 在 UI 執行緒上使用手寫筆外掛程式執行操作  
 因為精確的點擊測試不能在畫筆執行緒上執行，所以有些項目可能有時會接收到其他項目的手寫筆輸入。  如果您要在執行操作前先確認輸入的傳送正確，請訂閱 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>、<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A> 或 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> 方法，並在該方法中執行操作。  這些方法是在執行精確的點擊測試後，由應用程式執行緒所叫用。  如果要訂閱這些方法，請在畫筆執行緒上發生的方法中呼叫 <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> 方法。  
  
 下圖按照 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 的手寫筆事件，說明畫筆執行緒及 UI 執行緒之間的關係。  
  
 ![筆跡執行緒模型 &#40;UI 和 Pen&#41;](../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading\_PluginCallbacks")  
  
## 呈現筆墨  
 當使用者繪製筆劃時，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會在個別執行緒上呈現筆墨，所以即使當 UI 執行緒忙碌時，筆墨也會像是「順著」畫筆出現一樣顯示。  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會在動態呈現執行緒收集手寫筆的點時，在此執行緒上建置一個視覺化樹狀目錄。  當使用者完成筆劃時，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會要求當應用程式執行下一個呈現動作時要收到通知。  當應用程式完成下一個呈現動作時，<xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 就會清除視覺化樹狀目錄。  下列圖表說明這個程序。  
  
 ![筆跡執行緒圖表](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading\_VisualTree")  
  
1.  使用者開始筆劃。  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會建立視覺化樹狀目錄。  
  
2.  使用者繪製筆劃。  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會建置視覺化樹狀目錄。  
  
3.  使用者結束筆劃。  
  
    1.  <xref:System.Windows.Controls.InkPresenter> 會將筆劃加入至它的視覺化樹狀目錄。  
  
    2.  媒體整合層 \(Media Integration Layer，MIL\) 會靜態呈現筆劃。  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 會清除視覺效果。