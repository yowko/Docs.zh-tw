---
title: "最佳化效能：資料繫結 | Microsoft Docs"
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
  - "資料繫結, 效能"
  - "資料繫結, 效能"
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 最佳化效能：資料繫結
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結在資料的展示和互動上，提供應用程式簡單而一致的方式。  您可以 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件和 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 的形式將不同資料來源的項目繫結至資料。  
  
 本主題提供資料繫結的效能建議。  
  
   
  
<a name="HowDataBindingReferencesAreResolved"></a>   
## 資料繫結參考的解析方式  
 在討論資料繫結的效能問題以前，應該花點時間了解 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結引擎是怎麼樣解析繫結的物件參考。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結的來源可以是任何 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件。  您可以繫結至 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件的屬性、子屬性或索引子 \(Indexer\)。  使用 [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] 反映 \(Reflection\) 或 <xref:System.ComponentModel.ICustomTypeDescriptor> 都可以解析繫結參考。  以下是三種解析物件繫結參考的方法。  
  
 第一個方法使用到反映。  在這種情況下，會使用 <xref:System.Reflection.PropertyInfo> 物件來尋找屬性 \(Property\) 的屬性 \(Attribute\)，並存取屬性 \(Property\) 的中繼資料 \(Metadata\)。  使用 <xref:System.ComponentModel.ICustomTypeDescriptor> 介面時，資料繫結引擎會用這個介面存取屬性 \(Property\) 的值。  在物件沒有靜態屬性集的情況下，<xref:System.ComponentModel.ICustomTypeDescriptor> 介面特別有用。  
  
 實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面或使用與 <xref:System.ComponentModel.TypeDescriptor> 相關聯的變更告知，都可以提供屬性 \(Property\) 變更告知。  但是，若要實作屬性 \(Property\) 變更告知，使用 <xref:System.ComponentModel.INotifyPropertyChanged> 是較好的策略。  
  
 如果來源物件是 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件，且來源屬性 \(Property\) 是 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性，則 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結引擎必須先對來源物件使用反映以取得 <xref:System.ComponentModel.TypeDescriptor>，然後再查詢 <xref:System.ComponentModel.PropertyDescriptor>。  從效能的觀點來看，整個反映作業程序可能非常耗費時間。  
  
 解析物件參考的第二個方法牽涉到實作了 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 來源物件，以及屬於 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性的來源屬性。  在這種情況中，資料繫結引擎直接對來源型別使用反映，並取得所需的屬性。  這依然不是最佳方法，但所花費的工作集需求比第一個方法要少。  
  
 解析物件參考的第三個方法牽涉到屬於 <xref:System.Windows.DependencyObject> 的來源物件，以及屬於 <xref:System.Windows.DependencyProperty> 的來源屬性。  在這種情況中，資料繫結引擎不必使用反映，  而是由屬性引擎和資料繫結引擎一起獨立解析屬性參考。  這是解析用於進行資料繫結之物件參考的最佳方法。  
  
 下表比較對有一千個 <xref:System.Windows.Controls.TextBlock> 項目的 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性進行資料繫結時，三種方法的速度。  
  
|**繫結 TextBlock 的 Text 屬性**|**繫結時間 \(毫秒\)**|**轉譯時間 \-\- 包括繫結 \(毫秒\)**|  
|--------------------------------|---------------------|-------------------------------|  
|至 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件的屬性|115|314|  
|至實作 <xref:System.ComponentModel.INotifyPropertyChanged> 之 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件的屬性|115|305|  
|至 <xref:System.Windows.DependencyObject> 的 <xref:System.Windows.DependencyProperty>|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## 繫結至大型 CLR 物件  
 當您將資料繫結至有上千個屬性的單一 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件時，會對效能造成嚴重的影響。  您可以將這單一物件分成數個擁有較少屬性的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件，就可以減少影響。  下表是將資料繫結至單一大型 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件和數個較小物件的繫結和轉譯時間。  
  
|**1000 個 TextBlock 物件的資料繫結**|**繫結時間 \(毫秒\)**|**轉譯時間 \-\- 包括繫結 \(毫秒\)**|  
|----------------------------------|---------------------|-------------------------------|  
|至含有 1000 個屬性的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件|950|1200|  
|至 1000 個含有單一屬性的 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## 繫結至 ItemsSource  
 請試想一個案例：您有一個 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> 物件，其中包含您想在 <xref:System.Windows.Controls.ListBox> 中顯示的員工清單。  為了要建立這兩個物件的對應關係，您將員工清單繫結至 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性。  但是，假設有個新員工加入您的群組。  您可能認為要在您已繫結的 <xref:System.Windows.Controls.ListBox> 值中插入這個新員工，只要將這個員工加入至您的員工清單中，資料繫結引擎就會自動辨認這個變更。  但這個想法是錯的；事實上，<xref:System.Windows.Controls.ListBox> 中並不會自動反映這個變更。  這是因為 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> 物件不會自動引發集合變更事件。  為了讓 <xref:System.Windows.Controls.ListBox> 採用變更，您必須重新建立員工清單，再重新附加至 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 屬性。  雖然這個解決方法有效，但是會嚴重影響效能。  每次當您重新指派 <xref:System.Windows.Controls.ListBox> 的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 給新物件，<xref:System.Windows.Controls.ListBox> 就會先丟掉它原來的項目，再重新產生整個清單。  如果您的 <xref:System.Windows.Controls.ListBox> 對應至複雜的 <xref:System.Windows.DataTemplate>，對效能的影響就會很大。  
  
 若要解決這個問題，一個非常有效的方法是將您的員工清單變成 <xref:System.Collections.ObjectModel.ObservableCollection%601>。  <xref:System.Collections.ObjectModel.ObservableCollection%601> 物件會引發變更告知供繫結引擎接收。  事件會從 <xref:System.Windows.Controls.ItemsControl> 中加入或移除一個項目，而不需重新產生整個清單。  
  
 下表顯示加入一個項目後，更新 <xref:System.Windows.Controls.ListBox> 需要的時間 \(在 UI 虛擬化功能關閉的情況下\)。  第一列中的數字是表示當 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> 物件繫結至 <xref:System.Windows.Controls.ListBox> 項目的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 時的耗用時間。  第二列中的數字是表示當 <xref:System.Collections.ObjectModel.ObservableCollection%601> 繫結至 <xref:System.Windows.Controls.ListBox> 項目的 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 時的耗用時間。  您可以發現，使用 <xref:System.Collections.ObjectModel.ObservableCollection%601> 資料繫結策略可以明顯節省許多時間。  
  
|**ItemsSource 的資料繫結**|**1 個項目的更新時間 \(毫秒\)**|  
|---------------------------|---------------------------|  
|至 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> 物件|1656|  
|至 <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## 將 IList 繫結至 ItemsControl 而非 IEnumerable  
 如果您可以選擇要將 <xref:System.Collections.Generic.IList%601> 還是 <xref:System.Collections.IEnumerable> 繫結至 <xref:System.Windows.Controls.ItemsControl> 物件，請選擇 <xref:System.Collections.Generic.IList%601> 物件。  將 <xref:System.Collections.IEnumerable> 繫結至 <xref:System.Windows.Controls.ItemsControl> 會強制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 建立一個包裝函式 <xref:System.Collections.Generic.IList%601> 物件，這表示您的效能會受到第二個物件的負荷的不必要影響。  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## 請不要為了資料繫結將 CLR 物件轉換為 XML  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 讓您可以將資料繫結至 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 內容，但是將資料繫結至 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 內容會比將資料繫結至 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件更慢。  如果資料繫結是唯一的目的，請不要將 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 物件資料轉換為 XML。  
  
## 請參閱  
 [最佳化 WPF 應用程式效能](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [應用程式效能規劃](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [運用硬體](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [配置與設計](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D 圖形和影像](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [物件行為](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [應用程式資源](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [文字](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [其他效能建議](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [逐步解說：在 WPF 應用程式中快取應用程式資料](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)