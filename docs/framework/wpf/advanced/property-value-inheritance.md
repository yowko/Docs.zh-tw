---
title: "屬性值繼承 | Microsoft Docs"
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
  - "繼承, 屬性值"
  - "屬性, 值繼承"
  - "值繼承"
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 屬性值繼承
屬性值繼承是 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統的功能。  屬性值繼承可以讓項目樹狀結構中的子項目從父項目取得特定屬性的值，繼承的值就如同在最近的父項目上設定的值。  而父項目也可能是透過屬性值繼承而取得值的，所以系統很可能會一路遞迴到頁面根項目。  屬性值繼承並不是預設的屬性系統行為，屬性必須使用特定的中繼資料設定來建立，才能讓該屬性啟始子項目的屬性值繼承。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## 屬性值繼承是內含項目繼承  
 這裡的「繼承」一詞，跟型別內容和一般物件導向程式設計中的繼承概念不完全一樣，那裡的衍生類別會從基底類別繼承成員定義。  那個繼承的意義在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中也適用：各種基底類別中定義的屬性 \(Property\)，在做為項目使用時會公開為衍生 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 類別的屬性 \(Attribute\)，對於程式碼則公開為成員。  屬性值繼承是特別針對屬性值如何以項目樹狀結構內的父子關係為基礎，從一個項目繼承到另一個項目。  能夠最直接看到該項目樹狀結構的時機是，當您在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中定義應用程式時將項目做為其他項目內的巢狀結構。  藉由將物件加入到指定的其他物件集合，也可以建立物件的樹狀結構，而屬性值繼承在執行階段的運作方式與完成的樹狀結構中一樣。  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## 屬性值繼承的實際應用  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] 包含數種啟用屬性繼承的屬性。  通常這些屬性的案例是，當包含屬性的地方每頁只適合設定一次屬性，但該屬性也是基底項目類別的成員，因此在大部分的子項目上也應該存在該屬性。  舉例來說，<xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性會控制非固定格式內容在頁面上應該展示和排列的方向。  通常，您會希望在所有子項目上以一致的方式處理文字流動的概念。  如果基於某個原因，在某個項目樹狀結構階層中由使用者或環境動作重設過流動方向，通常應該要對整體重設。  當 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 屬性設計是繼承的，則只要在項目樹狀結構中包含應用程式每頁的展示需求的層級上，設定或重設一次值即可。  即使是初始的預設值也將以這個方式繼承。  對於極少數具有混合流動方向設計的情況，屬性值繼承模型仍然可以讓個別項目重設值。  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## 讓自訂屬性可繼承  
 藉由變更自訂屬性的中繼資料，您也可以讓自己的自訂屬性成為可繼承的。  但是請注意，將屬性指定為可繼承確實會有某些效能考量。  當屬性沒有建立的區域值，或是透過樣式、樣板或資料繫結取得的值的情況下，可繼承的屬性會提供其指派屬性值給邏輯樹狀結構中的所有子項目。  
  
 若要讓屬性可以參與值的繼承，請依照 [註冊附加屬性](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)中的描述建立自訂附加屬性。  使用中繼資料 \(<xref:System.Windows.FrameworkPropertyMetadata>\) 註冊屬性，並在該中繼資料內的選項設定中指定 "Inherits" 選項。  此外，也要確定屬性具有建立的預設值，因為現在需要有該值可供繼承。  雖然是將屬性註冊為附加，您可能也想要建立屬性「包裝函式」，用於對擁有者型別的取得\/設定的存取，就如同您會對「非附加」[相依性屬性](GTMT)所做的。  完成這些作業後，可繼承的屬性的設定可以藉由這些方式達成：在擁有者型別或衍生型別上使用直接屬性包裝函式，或是對任何 <xref:System.Windows.DependencyObject> 使用附加屬性語法。  
  
 附加屬性在概念上與全域屬性類似，您可以檢查任何 <xref:System.Windows.DependencyObject> 的值並取得有效結果。  附加屬性的典型案例是對子項目設定屬性值，而當討論中的屬性是一定會隱含呈現為樹狀結構每個項目 \(<xref:System.Windows.DependencyObject>\) 上的附加屬性時，這個案例更為有效。  
  
> [!NOTE]
>  雖然屬性值繼承看起來也適用於非附加相依性屬性，卻沒有定義透過執行階段樹狀結構中某些項目界限的非附加屬性的繼承行為。  在您於中繼資料內指定 <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> 的地方，請一定要使用 <xref:System.Windows.DependencyProperty.RegisterAttached%2A> 註冊屬性。  
  
<a name="InheritanceContext"></a>   
## 跨樹狀結構界限繼承屬性值  
 屬性繼承是藉由周遊項目樹狀結構而運作的。  這個樹狀結構通常與邏輯樹狀結構平行。  然而，每當您在定義項目樹狀結構的標記中包含 [WPF 核心層級](GTMT)物件時，例如 <xref:System.Windows.Media.Brush>，您就建立了不連續的邏輯樹狀結構。  真正的邏輯樹狀結構在概念上不會透過 <xref:System.Windows.Media.Brush> 擴充，因為邏輯樹狀結構是 [WPF 架構層級](GTMT)的概念。  您可以在使用 <xref:System.Windows.LogicalTreeHelper> 的方法時看到這個反映結果。  然而，屬性值繼承可以做為邏輯樹狀結構中這個缺口的橋樑，並且仍然可以傳遞繼承值，只要可繼承的屬性是註冊為附加屬性，而且沒有遇到刻意設定的繼承封鎖界限 \(例如 <xref:System.Windows.Controls.Frame>\)。  
  
## 請參閱  
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)   
 [相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)