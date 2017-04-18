---
title: "攔截手寫筆的輸入 | Microsoft Docs"
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
  - "架構, System.Windows.Input.StylusPlugIns"
  - "InkCanvas, 將外掛程式加入至"
  - "外掛程式, 手寫筆"
  - "StylusPlugIns 架構"
  - "System.Windows.Input.StylusPlugIns 架構"
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 攔截手寫筆的輸入
<xref:System.Windows.Input.StylusPlugIns> 架構提供一套機制，可以實作 <xref:System.Windows.Input.Stylus> 輸入的低階控制並且建立數位筆墨 <xref:System.Windows.Ink.Stroke> 物件。  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 類別提供一種機制，讓您實作自訂行為，並且可以將自訂行為套用到手寫筆裝置所傳入的資料流以達到最佳效能。  
  
 本主題包含下列子章節：  
  
-   [架構](#Architecture)  
  
-   [實作手寫筆外掛程式](#ImplementingStylusPlugins)  
  
-   [將外掛程式加入 InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
-   [結論](#Conclusion)  
  
<a name="Architecture"></a>   
## 架構  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 由 [StylusInput](http://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) API 演進而來，如 [Microsoft Windows XP Tablet PC Edition Software Development Kit 1.7](http://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409) 中的[存取及管理畫筆輸入Accessing and Manipulating Pen Input](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409) 所述。  
  
 每個 <xref:System.Windows.UIElement> 都有做為 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性。  您可以將 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 加入項目的 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性以操作所產生的 <xref:System.Windows.Input.StylusPoint> 資料。  <xref:System.Windows.Input.StylusPoint>資料是由系統數位板支援的所有屬性組成，包含 <xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint.Y%2A> 點資料和 <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> 資料。  
  
 當您將 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 加入 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性時，<xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 物件會直接插入來自 <xref:System.Windows.Input.Stylus> 裝置的資料流。  將外掛程式加入 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合的順序表示他們接收 <xref:System.Windows.Input.StylusPoint> 資料的順序。  例如，如果您將限制輸入的篩選外掛程式加入特定區域，然後加入可辨識撰寫動作的外掛程式，可辨識動作的外掛程式會接收到篩選的 <xref:System.Windows.Input.StylusPoint> 資料。  
  
<a name="ImplementingStylusPlugins"></a>   
## 實作手寫筆外掛程式  
 若要實作衍生自 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 的類別。  此類別會在資料流來自於 <xref:System.Windows.Input.Stylus> 時應用資料流。  在此類別中，您可以修改 <xref:System.Windows.Input.StylusPoint> 資料的值。  
  
> [!CAUTION]
>  如果 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 擲出或造成例外狀況，應用程式就會關閉。  您應該徹底測試使用 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 的控制項，並且只有在確定 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 不會擲出例外狀況時，才使用控制項。  
  
 下列範例會在資料來自於 <xref:System.Windows.Input.Stylus> 裝置時，修改 <xref:System.Windows.Input.StylusPoint> 資料中的 <xref:System.Windows.Input.StylusPoint.X%2A> 和 <xref:System.Windows.Input.StylusPoint.Y%2A> 值，藉以示範限制手寫筆輸入的外掛程式。  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## 將外掛程式加入 InkCanvas  
 使用自訂外掛程式最簡單的方法是實作衍生自 InkCanvas 的類別並將它加入 <xref:System.Windows.UIElement.StylusPlugIns%2A> 屬性。  
  
 下列範例示範篩選筆墨的自訂 <xref:System.Windows.Controls.InkCanvas>。  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 如果您將 `FilterInkCanvas` 加入應用程式並加以執行，您便會發現在使用者完成筆劃之前，筆墨並不會限制在某一區域中。  這是因為 <xref:System.Windows.Controls.InkCanvas> 擁有 <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> 屬性，其為 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 且已經是 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合的成員。  您加入 <xref:System.Windows.UIElement.StylusPlugIns%2A> 集合的自訂 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 會在 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 接收資料之後，接收 <xref:System.Windows.Input.StylusPoint> 資料。  因此，在使用者提起手寫筆結束筆劃之前，都不會篩選 <xref:System.Windows.Input.StylusPoint> 資料。  若要在使用者繪製筆墨時進行篩選，您必須在 <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> 之前插入 `FilterPlugin`。  
  
 下列 C\# 程式碼會示範自訂 <xref:System.Windows.Controls.InkCanvas>，會在繪製筆墨時進行篩選。  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## 結論  
 您可以衍生專屬的 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> 類別並將這些類別插入 <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> 集合，藉此大幅強化數位筆墨的行為。  您可以在產生 <xref:System.Windows.Input.StylusPoint> 資料時進行存取，讓您有機會自訂 <xref:System.Windows.Input.Stylus> 輸入。  因為您對 <xref:System.Windows.Input.StylusPoint> 資料的存取權限非常低，所以能夠以最佳的應用程式效能，實作筆墨收集並且呈現筆墨。  
  
## 請參閱  
 [筆墨進階處理](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)   
 [存取及管理畫筆輸入](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)