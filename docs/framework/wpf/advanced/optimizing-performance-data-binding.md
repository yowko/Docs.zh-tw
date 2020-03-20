---
title: 最佳化效能：資料繫結
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 3128f453378f9d74f867b571e30f2be4e8add8a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186751"
---
# <a name="optimizing-performance-data-binding"></a>最佳化效能：資料繫結
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結在資料的展示和互動上，提供應用程式簡單而一致的方式。 元素可以綁定到來自各種資料來源的資料，其形式是 CLR 物件和 XML。  
  
 本主題提供資料繫結的效能建議。  

<a name="HowDataBindingReferencesAreResolved"></a>
## <a name="how-data-binding-references-are-resolved"></a>資料繫結參考的解析方式  
 在討論資料繫結效能問題之前，值得先探討 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結引擎如何解析物件參考以進行繫結。  
  
 資料繫結的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]源可以是任何 CLR 物件。 您可以綁定到 CLR 物件的屬性、子屬性或索引子。 使用 Microsoft .NET 框架反射或 解析綁定引用<xref:System.ComponentModel.ICustomTypeDescriptor>。 以下是三種解析繫結用之物件參考的方法。  
  
 第一個方法涉及使用反映。 在這種情況下，<xref:System.Reflection.PropertyInfo>物件用於發現屬性的屬性並提供對屬性中繼資料的訪問。 使用<xref:System.ComponentModel.ICustomTypeDescriptor>介面時，資料繫結引擎使用此介面訪問屬性值。 在<xref:System.ComponentModel.ICustomTypeDescriptor>物件沒有靜態屬性集的情況下，該介面特別有用。  
  
 屬性更改通知可以通過實現<xref:System.ComponentModel.INotifyPropertyChanged>介面或使用 與 關聯的更改通知來提供。 <xref:System.ComponentModel.TypeDescriptor> 但是，實現屬性更改通知的首選策略是使用<xref:System.ComponentModel.INotifyPropertyChanged>。  
  
 如果源物件是 CLR 物件，並且源屬性是 CLR 屬性，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]則資料繫結引擎必須首先使用對源物件的反射來獲取 ，<xref:System.ComponentModel.TypeDescriptor>然後查詢 。 <xref:System.ComponentModel.PropertyDescriptor> 這個反映作業序列從效能觀點來看可能非常耗時。  
  
 解析物件引用的第二種方法涉及實現介面的<xref:System.ComponentModel.INotifyPropertyChanged>CLR 源物件和作為 CLR 屬性的源屬性。 在此情況下，資料繫結引擎會直接對來源類型使用反映，並取得必要的屬性。 這仍不是最佳的方法，但它的工作集需求的成本會比第一種方法低。  
  
 解析物件引用的第三種方法涉及源物件，該物件是<xref:System.Windows.DependencyObject>和 源屬性<xref:System.Windows.DependencyProperty>。 在此情況下，資料繫結引擎不必使用反映。 相反地，屬性引擎和資料繫結引擎會一起獨立解析屬性參考。 這是解析用於資料繫結之物件參考的最佳方法。  
  
 下表比較了使用這三種方法綁定一千<xref:System.Windows.Controls.TextBlock.Text%2A><xref:System.Windows.Controls.TextBlock>個元素屬性的資料速度。  
  
|**繫結 TextBlock 的 Text 屬性**|**繫結時間 (毫秒)**|**轉譯時間 -- 包括繫結 (毫秒)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|到 CLR 物件的屬性|115|314|  
|到實現的 CLR 物件的屬性<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|到<xref:System.Windows.DependencyProperty>的<xref:System.Windows.DependencyObject>。|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>
## <a name="binding-to-large-clr-objects"></a>繫結至大型 CLR 物件  
 當資料繫結到具有數千個屬性的單個 CLR 物件時，將顯著的性能影響。 通過將單個物件劃分為多個具有較少屬性的 CLR 物件，可以最大程度地減少此影響。 該表顯示了與多個較小物件綁定到單個大型 CLR 物件的資料的綁定和呈現時間。  
  
|**資料繫結 1000 個 TextBlock 物件**|**繫結時間 (毫秒)**|**轉譯時間 -- 包括繫結 (毫秒)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|到具有 1000 個屬性的 CLR 物件|950|1200|  
|到具有一個屬性的 1000 個 CLR 物件|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>
## <a name="binding-to-an-itemssource"></a>繫結至 ItemsSource  
 請考慮一個方案，其中 CLR<xref:System.Collections.Generic.List%601>物件包含要在 中顯示的員工清單。 <xref:System.Windows.Controls.ListBox> 要在這兩個物件之間創建對應關係，您可以將員工清單綁定到<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>的屬性。 <xref:System.Windows.Controls.ListBox> 不過，假設您有新的員工加入您的群組。 您可能認為，為了將此人插入到綁定<xref:System.Windows.Controls.ListBox>值中，只需將此人添加到您的員工清單中，並期望資料繫結引擎自動識別此更改。 這一假設將被證明是錯誤的;實際上，更改不會自動反映在 中<xref:System.Windows.Controls.ListBox>。 這是因為 CLR<xref:System.Collections.Generic.List%601>物件不會自動引發集合更改的事件。 要獲取 更改<xref:System.Windows.Controls.ListBox>，必須重新創建員工清單，並將其<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>重新附加到 的屬性。 <xref:System.Windows.Controls.ListBox> 雖然這個解決方案有效，但它造成了嚴重的效能影響。 每次將 的<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>重新<xref:System.Windows.Controls.ListBox>分配給新物件時，<xref:System.Windows.Controls.ListBox>第一個物件都會放棄其以前的項並重新生成其整個清單。 如果將<xref:System.Windows.Controls.ListBox>性能影響映射到複雜位置<xref:System.Windows.DataTemplate>，則性能影響將放大。  
  
 解決這個問題的一個非常有效的方法是使員工清單成為<xref:System.Collections.ObjectModel.ObservableCollection%601>. 物件<xref:System.Collections.ObjectModel.ObservableCollection%601>將引發資料繫結引擎可以接收的更改通知。 事件從 中添加或刪除項，<xref:System.Windows.Controls.ItemsControl>而無需重新生成整個清單。  
  
 下表顯示了添加一<xref:System.Windows.Controls.ListBox>個專案時更新（關閉 UI 虛擬化）所需的時間。 第一行中的數位表示 CLR<xref:System.Collections.Generic.List%601>物件綁定到<xref:System.Windows.Controls.ListBox>元素 的<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>時經過的時間。 第二行中的數位表示綁定到<xref:System.Collections.ObjectModel.ObservableCollection%601><xref:System.Windows.Controls.ListBox>元素 的<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>時經過的時間。 請注意使用<xref:System.Collections.ObjectModel.ObservableCollection%601>資料繫結策略顯著節省時間。  
  
|**資料繫結 ItemsSource**|**1 個項目的更新時間 (毫秒)**|  
|--------------------------------------|---------------------------------------|  
|到 CLR<xref:System.Collections.Generic.List%601>物件|1656|  
|到<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>將 IList 繫結至 ItemsControl 而非 IEnumerable  
 如果在將 物件綁定 為<xref:System.Collections.Generic.IList%601>物件或<xref:System.Collections.IEnumerable><xref:System.Windows.Controls.ItemsControl>物件之間可以選擇，請選擇<xref:System.Collections.Generic.IList%601>該物件。 綁定<xref:System.Collections.IEnumerable>到<xref:System.Windows.Controls.ItemsControl>強制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]以創建包裝<xref:System.Collections.Generic.IList%601>物件，這意味著您的性能受到第二個物件的不必要的開銷的影響。  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>不要只為了資料繫結而將 CLR 物件轉換成 XML。  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]允許您將資料繫結到 XML 內容;但是，與對 CLR 物件綁定的資料繫結速度要慢。 如果唯一的目的是資料繫結，則不要將 CLR 物件資料轉換為 XML。  
  
## <a name="see-also"></a>另請參閱

- [最佳化 WPF 應用程式效能](optimizing-wpf-application-performance.md)
- [應用程式效能規劃](planning-for-application-performance.md)
- [運用硬體](optimizing-performance-taking-advantage-of-hardware.md)
- [版面配置與設計](optimizing-performance-layout-and-design.md)
- [2D 圖形和影像處理](optimizing-performance-2d-graphics-and-imaging.md)
- [物件行為](optimizing-performance-object-behavior.md)
- [應用程式資源](optimizing-performance-application-resources.md)
- [文本](optimizing-performance-text.md)
- [其他效能建議](optimizing-performance-other-recommendations.md)
- [資料繫結概述](../../../desktop-wpf/data/data-binding-overview.md)
- [逐步解說：在 WPF 應用程式中快取應用程式資料](walkthrough-caching-application-data-in-a-wpf-application.md)
