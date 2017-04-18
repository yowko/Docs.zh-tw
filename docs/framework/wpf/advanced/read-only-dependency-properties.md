---
title: "唯讀相依性屬性 | Microsoft Docs"
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
  - "相依性屬性, 唯讀"
  - "唯讀相依性屬性"
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 唯讀相依性屬性
本主題說明唯讀相依性屬性，包括現有的唯讀相依性屬性，以及建立自訂唯讀相依性屬性的案例和技巧。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已了解實作相依性屬性的基本案例，以及中繼資料 \(Metadata\) 套用至自訂相依性屬性的方式。  如需相關內容，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)和[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  
  
<a name="existing"></a>   
## 現有的唯讀相依性屬性  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 架構中定義的某些相依性屬性是唯讀屬性。  指定唯讀相依性屬性的原因通常是因為它們是判斷狀態時應該使用的屬性，但是該狀態受到許多因素影響，而就使用者介面設定的觀點而言，只將屬性設定為該狀態並不恰當。  例如，<xref:System.Windows.UIElement.IsMouseOver%2A> 屬性實際上只是從滑鼠輸入來判斷的表面狀態。  嘗試透過規避實際的滑鼠輸入，改以程式設計方式設定這個值，都會產生無法預測且不一致的結果。  
  
 由於具有無法設定的特性，唯讀相依性屬性並不適用於相依性屬性通常可提供解決方案的許多案例 \(也就是資料繫結 \(Data Binding\)、可直接設定樣式的值、驗證、動畫、繼承 \(Inheritance\)\)。  雖然無法設定，但是唯讀相依性屬性仍然具有屬性系統中相依性屬性所支援的某些額外功能。  其保留的最重要一項功能就是唯讀相依性屬性還是可以當做樣式中的屬性觸發程序 \(Trigger\)。  您不能使用一般的 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性來啟用觸發程序；此屬性必須是相依性屬性。  前面提到的 <xref:System.Windows.UIElement.IsMouseOver%2A> 屬性是最佳的案例範例；如果使用者將滑鼠放在控制項定義的某個區域時，控制項內複合項目的某些可見屬性 \(例如背景、前景或類似屬性\) 就會變更，這個屬性就可能相當適合用來定義這種控制項的樣式。  唯讀相依性屬性中的變更也可以由屬性系統固有的失效處理序 \(Process\) 加以偵測及回報，而實際上這項功能也提供屬性觸發程序功能的內部支援。  
  
<a name="new"></a>   
## 建立自訂唯讀相依性屬性  
 請務必詳讀前一節，了解唯讀相依性不適用於許多一般相依性屬性案例的原因。  不過，若有適當的案例，您還是可以建立自己的唯讀相依性屬性。  
  
 建立唯讀相依性屬性的程序大部分與[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)和 [實作相依性屬性](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md)等主題說明的程序相同。  主要的差異有三個：  
  
-   註冊屬性時，請呼叫 <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> 方法，而非屬性註冊的一般 <xref:System.Windows.DependencyProperty.Register%2A> 方法。  
  
-   實作 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]「包裝函式」屬性時，請確定包裝函式也沒有 set 實作，如此您所公開的公用 \(Public\) 包裝函式才不會產生不一致的唯讀狀態。  
  
-   唯讀註冊所傳回的屬性是 <xref:System.Windows.DependencyPropertyKey>，而不是 <xref:System.Windows.DependencyProperty>。  您還是應該將這個欄位儲存為成員，但是通常不會將它設定該型別的公用成員。  
  
 您用來支援唯讀相依性屬性的任何私用 \(Private\) 欄位或值當然都可以使用您所決定的任何邏輯來撰寫。  不過，設定屬性 \(不論是初次設定或做為執行階段邏輯一部分\) 最直接的方法是使用屬性系統的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，而不是避開屬性系統，直接設定私用支援欄位。  特別是有一個 <xref:System.Windows.DependencyObject.SetValue%2A> 的簽章 \(Signature\) 可以接受型別 <xref:System.Windows.DependencyPropertyKey> 的參數。  您在應用程式邏輯內以程式設計方式設定這個值的方法和位置，將會影響您希望如何設定第一次註冊相依性屬性時所建立之 <xref:System.Windows.DependencyPropertyKey> 的存取權。  如果您完全在類別內處理這個邏輯，可以將它設定為私用；如果需要從組件的其他部分設定，則可將它設定為內部。  其中一種方法是在通知類別執行個體必須變更儲存屬性之相關事件的類別事件處理常式 \(Event Handler\) 內呼叫 <xref:System.Windows.DependencyObject.SetValue%2A>。  另一種方法則是在註冊過程中，使用成對的 <xref:System.Windows.PropertyChangedCallback> 和 <xref:System.Windows.CoerceValueCallback> 回呼 \(Callback\) 做為相依性屬性的中繼資料一部分，將這些屬性結合在一起。  
  
 因為 <xref:System.Windows.DependencyPropertyKey> 是私用的，而且不會由屬性系統傳送到程式碼外部，所以相較於可讀寫的相依性屬性，唯讀相依性屬性的安全性設定確實較為完善。  對於可讀寫的相依性屬性，識別欄位是明確或隱含公用的欄位，因此屬性可做廣泛的設定。  如需詳細資訊，請參閱[相依性屬性的安全性](../../../../docs/framework/wpf/advanced/dependency-property-security.md)。  
  
## 請參閱  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)