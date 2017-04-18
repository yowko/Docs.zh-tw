---
title: "使用 DrawingVisual 物件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "視覺分層中的 DrawingVisual 物件"
  - "視覺分層, DrawingVisual 物件"
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 使用 DrawingVisual 物件
本主題提供如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 視覺分層中使用 <xref:System.Windows.Media.DrawingVisual> 物件的概觀。  
  
 本主題包含下列章節。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [DrawingVisual 物件](#drawing_visual_object)  
  
-   [DrawingVisual 裝載容器](#drawingvisual_host_container)  
  
-   [建立 DrawingVisual 物件](#creating_drawingvisual_objects)  
  
-   [建立 FrameworkElement 成員的覆寫](#creating_overrides)  
  
-   [提供點擊測試支援](#providing_hit_testing_support)  
  
-   [相關主題](#seeAlsoToggle)  
  
<a name="drawingvisual_object"></a>   
## DrawingVisual 物件  
 <xref:System.Windows.Media.DrawingVisual> 為輕量型繪圖類別，可用於轉譯圖案、影像或文字。  此類別因為不提供配置或事件處理，所以視為輕量類別，而配置或事件處理卻可改善其效能。  基於這個理由，繪圖適合用於背景或美工圖案。  
  
<a name="drawingvisual_host_container"></a>   
## DrawingVisual 裝載容器  
 若要使用 <xref:System.Windows.Media.DrawingVisual> 物件，您必須建立物件的裝載容器。  裝載容器物件必須衍生自 <xref:System.Windows.FrameworkElement> 類別，它會提供 <xref:System.Windows.Media.DrawingVisual> 類別所缺少的配置和事件處理支援。  裝載容器物件不會顯示任何可見屬性，因為它的主要用途是包含子物件。  不過，裝載容器的 <xref:System.Windows.UIElement.Visibility%2A> 屬性必須設為 <xref:System.Windows.Visibility>，否則就看不到它的任何子項目。  
  
 當您建立視覺物件的裝載容器物件時，必須將視覺物件參考儲存在 <xref:System.Windows.Media.VisualCollection> 中。  請使用 <xref:System.Windows.Media.VisualCollection.Add%2A> 方法將視覺物件加入到裝載容器中。  下列範例會建立裝載容器物件，並將三個視覺物件加入到它的 <xref:System.Windows.Media.VisualCollection>。  
  
 [!code-csharp[DrawingVisualSample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  如需擷取上述程式碼範例之來源的完整程式碼範例，請參閱[使用 DrawingVisual 進行點擊測試範例](http://go.microsoft.com/fwlink/?LinkID=159994) \(英文\)。  
  
<a name="creating_drawingvisual_objects"></a>   
## 建立 DrawingVisual 物件  
 <xref:System.Windows.Media.DrawingVisual> 物件剛建立時沒有繪圖內容。  您可以藉由擷取物件的 <xref:System.Windows.Media.DrawingContext> 並繪製到其中，以加入文字、圖形或影像內容。  <xref:System.Windows.Media.DrawingContext> 可藉由呼叫 <xref:System.Windows.Media.DrawingVisual> 物件的 <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> 方法傳回。  
  
 若要將矩形繪製到 <xref:System.Windows.Media.DrawingContext> 中，請使用 <xref:System.Windows.Media.DrawingContext> 物件的 <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> 方法。  您也可以使用類似的方法繪製其他類型的內容。  將內容繪製到 <xref:System.Windows.Media.DrawingContext> 後，請呼叫 <xref:System.Windows.Media.DrawingContext.Close%2A> 方法，以關閉 <xref:System.Windows.Media.DrawingContext> 和保存此內容。  
  
 下列範例會建立 <xref:System.Windows.Media.DrawingVisual> 物件，並將矩形繪製到它的 <xref:System.Windows.Media.DrawingContext>。  
  
 [!code-csharp[DrawingVisualSample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## 建立 FrameworkElement 成員的覆寫  
 裝載容器負責管理它的視覺物件集合。  這需要裝載容器實作衍生 <xref:System.Windows.FrameworkElement> 類別的成員覆寫。  
  
 下列清單描述必須覆寫的兩個成員：  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>：從子項目集合傳回位於指定索引位置的子項目。  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>：取得這個項目內的視覺子項目數。  
  
 下列範例會實作兩個 <xref:System.Windows.FrameworkElement> 成員的覆寫。  
  
 [!code-csharp[DrawingVisualSample#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## 提供點擊測試支援  
 裝載容器物件即使不會顯示任何可見屬性，仍可提供事件處理，不過，它的 <xref:System.Windows.UIElement.Visibility%2A> 屬性必須設為 <xref:System.Windows.Visibility>。  這可讓您為裝載容器建立事件處理常式，以捕捉滑鼠事件，例如放開滑鼠左鍵。  事件處理常式接著可藉由叫用 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> 方法來實作點擊測試。  此方法的 <xref:System.Windows.Media.HitTestResultCallback> 參數會參考使用者定義的程序，您可使用該程序來判斷點擊測試的結果動作。  
  
 下列範例實作了裝載容器物件及其子項目的點擊測試支援。  
  
 [!code-csharp[DrawingVisualSample#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## 請參閱  
 <xref:System.Windows.Media.DrawingVisual>   
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>   
 [WPF 圖形轉譯概觀](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [視覺分層中的點擊測試](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)