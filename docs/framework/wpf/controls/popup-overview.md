---
title: "快顯功能表概觀 | Microsoft Docs"
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
  - "控制項, Popup"
  - "Popup 控制項 [WPF], 關於 Popup 控制項"
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# 快顯功能表概觀
<xref:System.Windows.Controls.Primitives.Popup> 控制項提供一種方式，在目前視窗上浮動的另一個視窗 \(座標相對於指定項目或螢幕座標\) 中顯示內容。  本主題將介紹 <xref:System.Windows.Controls.Primitives.Popup> 控制項，並提供其用途的相關資訊。  
  
   
  
<a name="What_Is_a_Popup_"></a>   
## 什麼是快顯功能表  
 快顯功能表是一個 <xref:System.Windows.Controls.Primitives.Popup> 控制項，可在座標相對於螢幕上某項目或某點的另一個視窗中顯示內容。  當 <xref:System.Windows.Controls.Primitives.Popup> 可見時，<xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 屬性是設為 `true`。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Primitives.Popup> 不會在滑鼠指標移至其父物件上時自動開啟。  若要讓 <xref:System.Windows.Controls.Primitives.Popup> 自動開啟，請使用 <xref:System.Windows.Controls.ToolTip> 或 <xref:System.Windows.Controls.ToolTipService> 類別。  如需詳細資訊，請參閱 [工具提示概觀](../../../../docs/framework/wpf/controls/tooltip-overview.md)。  
  
<a name="APopupExample"></a>   
## 建立快顯功能表  
 下列範例顯示如何定義屬於 <xref:System.Windows.Controls.Button> 控制項之子項目的 <xref:System.Windows.Controls.Primitives.Popup> 控制項。  由於 <xref:System.Windows.Controls.Button> 只能有一個子項目，因此這個範例會將 <xref:System.Windows.Controls.Button> 與 <xref:System.Windows.Controls.Primitives.Popup> 控制項的文字放在 <xref:System.Windows.Controls.StackPanel> 中。  <xref:System.Windows.Controls.Primitives.Popup> 的內容會出現在 <xref:System.Windows.Controls.TextBlock> 控制項中，這個控制項會將文字顯示在另一個視窗中，而這個視窗會在應用程式視窗上相關 <xref:System.Windows.Controls.Button> 控制項的附近浮動。  
  
 [!code-xml[PopupSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xml[PopupSimple#CreatePopupCodeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## 會實作快顯功能表的控制項  
 您可以將 <xref:System.Windows.Controls.Primitives.Popup> 控制項建到其他控制項中。  下列控制項可以實作特定用途的 <xref:System.Windows.Controls.Primitives.Popup> 控制項：  
  
-   <xref:System.Windows.Controls.ToolTip>.  若要建立某個項目的工具提示，請使用 <xref:System.Windows.Controls.ToolTip> 與 <xref:System.Windows.Controls.ToolTipService> 類別。  如需詳細資訊，請參閱 [工具提示概觀](../../../../docs/framework/wpf/controls/tooltip-overview.md)。  
  
-   <xref:System.Windows.Controls.ContextMenu>.  若要建立某個項目的內容功能表，請使用 <xref:System.Windows.Controls.ContextMenu> 控制項。  如需詳細資訊，請參閱 [ContextMenu 概觀](../../../../docs/framework/wpf/controls/contextmenu-overview.md)。  
  
-   <xref:System.Windows.Controls.ComboBox>.  若要建立具有可顯示或隱藏之下拉式清單方塊的選取控制項，請使用 <xref:System.Windows.Controls.ComboBox> 控制項。  
  
-   <xref:System.Windows.Controls.Expander>.  若要建立會顯示標題 \(具有會顯示內容的可摺疊式區域\) 的控制項，請使用 <xref:System.Windows.Controls.Expander> 控制項。  如需詳細資訊，請參閱 [Expander 概觀](../../../../docs/framework/wpf/controls/expander-overview.md)。  
  
<a name="PopupBehaviorandAppearance"></a>   
## 快顯功能表的行為與外觀  
 <xref:System.Windows.Controls.Primitives.Popup> 控制項提供讓您自訂其行為與外觀的功能。  例如，您可以設定開啟與關閉行為、動畫、不透明度與點陣圖效果，以及 <xref:System.Windows.Controls.Primitives.Popup> 大小與位置。  
  
<a name="OpenandCloseBehavior"></a>   
### 開啟與關閉行為  
 當 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 屬性設為 `true` 時，<xref:System.Windows.Controls.Primitives.Popup> 控制項會顯示其內容。  根據預設，<xref:System.Windows.Controls.Primitives.Popup> 在 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 屬性設為 `false` 之前，都會維持在開啟狀態。  但您可以藉由將 <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> 屬性設為 `false` 來變更這個預設行為。  當您將這個屬性設為 `false` 時，<xref:System.Windows.Controls.Primitives.Popup> 內容視窗會具有滑鼠捕捉 \(Mouse Capture\)。  當滑鼠事件發生於 <xref:System.Windows.Controls.Primitives.Popup> 視窗外時，<xref:System.Windows.Controls.Primitives.Popup> 即會失去滑鼠捕捉，且視窗會關閉。  
  
 當開啟或關閉 <xref:System.Windows.Controls.Primitives.Popup> 內容視窗時，會引發 <xref:System.Windows.Controls.Primitives.Popup.Opened> 與 <xref:System.Windows.Controls.Primitives.Popup.Closed> 事件。  
  
<a name="Animation"></a>   
### 動畫  
 <xref:System.Windows.Controls.Primitives.Popup> 控制項對於一般與淡入與滑入等行為相關聯的動畫，具有內建的支援。  您可以將 <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> 屬性設為 <xref:System.Windows.Controls.Primitives.PopupAnimation> 列舉值，以開啟這些動畫。  若要讓 <xref:System.Windows.Controls.Primitives.Popup> 動畫正確運作，您必須將 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> 屬性設為 `true`。  
  
 您也可以將 <xref:System.Windows.Media.Animation.Storyboard> 之類的動畫套用至 <xref:System.Windows.Controls.Primitives.Popup> 控制項。  
  
<a name="OpacityandBitmapEffects"></a>   
### 透明度與點陣圖效果  
 <xref:System.Windows.Controls.Primitives.Popup> 控制項的 <xref:System.Windows.UIElement.Opacity%2A> 屬性對其內容沒有任何作用。  根據預設，<xref:System.Windows.Controls.Primitives.Popup> 內容視窗為不透明。  若要建立透明的 <xref:System.Windows.Controls.Primitives.Popup>，請將 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> 屬性設為 `true`。  
  
 <xref:System.Windows.Controls.Primitives.Popup> 內容不會繼承您直接對父視窗中的 <xref:System.Windows.Controls.Primitives.Popup> 控制項或任何其他項目所設定的點陣圖效果，例如 <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>。  若要讓 <xref:System.Windows.Controls.Primitives.Popup> 內容顯示點陣圖效果，您必須直接對其內容設定點陣圖效果。  例如，如果 <xref:System.Windows.Controls.Primitives.Popup> 的子系為 <xref:System.Windows.Controls.StackPanel>，請對 <xref:System.Windows.Controls.StackPanel> 設定點陣圖效果。  
  
<a name="PopupSize"></a>   
### 快顯功能表大小  
 根據預設，<xref:System.Windows.Controls.Primitives.Popup> 會自動隨其內容調整大小。  當自動調整大小時，有些點陣圖效果可能會被隱藏，因為定義給 <xref:System.Windows.Controls.Primitives.Popup> 內容的預設螢幕區域大小並未提供足夠的空間來顯示點陣圖效果。  
  
 當您對內容設定 <xref:System.Windows.UIElement.RenderTransform%2A> 時，<xref:System.Windows.Controls.Primitives.Popup> 內容也可能變得不清楚。  在此情況下，如果轉換後的 <xref:System.Windows.Controls.Primitives.Popup> 內容超出原始 <xref:System.Windows.Controls.Primitives.Popup> 的區域，即可能隱藏部分內容。  如果點陣圖效果或轉換需要更多空間，您可以定義 <xref:System.Windows.Controls.Primitives.Popup> 內容周圍的邊界，為控制項提供更多空間。  
  
<a name="DefiningPopupPosition"></a>   
## 定義快顯功能表位置  
 您可以設定 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> 屬性，以放置快顯功能表。  如需詳細資訊，請參閱 [快顯功能表放置行為](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)。  當 <xref:System.Windows.Controls.Primitives.Popup> 顯示在螢幕上時，如果它的父項目已經重新調整位置的話，它就不會重新調整位置。  
  
<a name="CustomizingPopupPlacement"></a>   
### 自訂快顯功能表位置  
 您可以根據要顯示 <xref:System.Windows.Controls.Primitives.Popup> 的 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 指定一組相對的座標，以自訂 <xref:System.Windows.Controls.Primitives.Popup> 控制項的位置。  
  
 若要自訂位置，請將 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 屬性設為 <xref:System.Windows.Controls.Primitives.PlacementMode>。  接著，定義 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委派 \(Delegate\)，使其傳回 <xref:System.Windows.Controls.Primitives.Popup> 可以使用的一組位置點與主座標軸 \(依照優先順序\)。  系統會自動選取能夠顯示最多 <xref:System.Windows.Controls.Primitives.Popup> 部分的點。  如需範例，請參閱 [指定自訂 Popup 的位置](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md)。  
  
<a name="PopupandtheVisualTree"></a>   
## 快顯功能表與視覺化樹狀目錄  
 <xref:System.Windows.Controls.Primitives.Popup> 控制項沒有自己的[視覺化樹狀目錄](GTMT)，而是會在呼叫 <xref:System.Windows.Controls.Primitives.Popup> 的 <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> 方法時傳回大小 0 \(零\)。  不過，當您將 <xref:System.Windows.Controls.Primitives.Popup> 的 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 屬性設為 `true` 時，卻會建立擁有自己的視覺化樹狀目錄的新視窗。  這個新視窗包含 <xref:System.Windows.Controls.Primitives.Popup> 的 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 內容。  新視窗的寬度與高度不可超過螢幕寬度或高度的 75%。  
  
 <xref:System.Windows.Controls.Primitives.Popup> 控制項會以邏輯子系的形式維護其 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 內容的參考。  建立新視窗時，<xref:System.Windows.Controls.Primitives.Popup> 的內容會成為該視窗的視覺化子系，同時仍是 <xref:System.Windows.Controls.Primitives.Popup> 的邏輯子系。  相對地，<xref:System.Windows.Controls.Primitives.Popup> 仍是其 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 內容的邏輯父代 \(Parent\)。  
  
## 請參閱  
 <xref:System.Windows.Controls.Primitives.Popup>   
 <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>   
 <xref:System.Windows.Controls.Primitives.PlacementMode>   
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>   
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>   
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)