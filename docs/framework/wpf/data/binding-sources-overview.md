---
title: 繫結來源概觀
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
ms.openlocfilehash: 72ef84cb53c6eff1fc2fb9459b40e780869243a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62023776"
---
# <a name="binding-sources-overview"></a>繫結來源概觀
在資料繫結中，繫結來源物件是指您取得資料的來源物件。 本主題討論可以當做繫結來源的物件類型。  

<a name="binding_sources"></a>   
## <a name="binding-source-types"></a>繫結來源類型  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 資料繫結支援下列繫結來源類型：  
  
|繫結來源|描述|  
|--------------------|-----------------|  
|[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件|您可以繫結至任何[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 物件的公用屬性、子屬性和索引子。 繫結引擎會使用 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 反映取得這些屬性的值。 或者，物件實作<xref:System.ComponentModel.ICustomTypeDescriptor>或具有已註冊<xref:System.ComponentModel.TypeDescriptionProvider>也適用於繫結引擎。<br /><br /> 如需如何實作可做為繫結來源之類別的詳細資訊，請參閱本主題稍後的[為繫結來源實作類別](#classes)。|  
|動態物件|您可以繫結至可用的屬性與索引子的物件，實作<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。 如果您可以在程式碼中存取某個成員，就可以繫結至該成員。 例如，若動態物件可讓您在程式碼中透過 `someObjet.AProperty` 存取某個成員，您就可以將繫結路徑設定為 `AProperty`，以繫結至該成員。|  
|[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] 物件|您可以繫結至[!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)]物件，例如<xref:System.Data.DataTable>。 [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView>實作<xref:System.ComponentModel.IBindingList>介面，可提供繫結引擎所接聽的變更通知。|  
|[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 物件|您可以將繫結至並執行`XPath`上查詢<xref:System.Xml.XmlNode>， <xref:System.Xml.XmlDocument>，或<xref:System.Xml.XmlElement>。 便利的方式來存取[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]是在標記中的繫結來源的資料是使用<xref:System.Windows.Data.XmlDataProvider>物件。 如需詳細資訊，請參閱[使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。<br /><br /> 您也可以以繫結<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>，或繫結至這些類型的物件上執行使用 LINQ to XML 查詢的結果。 使用 LINQ to XML 來存取 XML 資料做為標記中的繫結來源的便利方式是使用<xref:System.Windows.Data.ObjectDataProvider>物件。 如需詳細資訊，請參閱[繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)。|  
|<xref:System.Windows.DependencyObject> 物件|您可以繫結至任何相依性屬性<xref:System.Windows.DependencyObject>。 如需範例，請參閱[繫結兩個控制項的屬性](how-to-bind-the-properties-of-two-controls.md)。|  
  
<a name="classes"></a>   
## <a name="implementing-a-class-for-the-binding-source"></a>為繫結來源實作類別  
 您可以建立自己的繫結來源。 本節討論在實作類別以做為繫結來源時必須知道的事。  
  
### <a name="providing-change-notifications"></a>提供變更通知  
 如果您使用其中一個<xref:System.Windows.Data.BindingMode.OneWay>或是<xref:System.Windows.Data.BindingMode.TwoWay>繫結 (因為您想要您[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]繫結來源屬性動態變更時更新)，您必須實作適當的屬性變更通知機制。 建議的機制是[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]或 動態類別實作<xref:System.ComponentModel.INotifyPropertyChanged>介面。 如需詳細資訊，請參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)。  
  
 如果您建立[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]未實作的物件<xref:System.ComponentModel.INotifyPropertyChanged>，則您必須安排自己的通知系統，以確定維持目前的繫結中的資料。 您可以針對想要通知變更的每個屬性支援 `PropertyChanged` 模式，以提供變更通知。 若要支援這個模式，請定義每個屬性的 *PropertyName*Changed 事件，其中 *PropertyName* 是屬性的名稱。 您可在每次屬性變更時，引發這個事件。  
  
 如果繫結來源實作其中一種通知機制，系統就會自動更新目標。 如果因故繫結來源不會提供適當的屬性變更通知，您可以選擇使用<xref:System.Windows.Data.BindingExpression.UpdateTarget%2A>方法來明確更新目標屬性。  
  
### <a name="other-characteristics"></a>其他特性  
 下列清單提供必須注意的其他重點：  
  
- 如果要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中建立物件，此類別必須擁有預設建構函式。 在某些[!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)]語言，例如C#，可能會為您建立的預設建構函式。  
  
- 要當做繫結之繫結來源屬性的屬性必須是類別的公用屬性。 明確定義的介面屬性不能做為繫結之用，而沒有基底實作的受保護、私用、內部或虛擬屬性同樣也不能做為繫結之用。  
  
- 您不能繫結至公用欄位。  
  
- 在類別中宣告的屬性，其型別就是傳遞至繫結的型別。 不過，繫結最終使用的型別需視繫結目標屬性 (而非繫結來源屬性) 的型別而定。 如果型別不同，您可能需要撰寫轉換器來處理自訂屬性一開始傳遞到繫結的方式。 如需詳細資訊，請參閱<xref:System.Windows.Data.IValueConverter>。  
  
<a name="objects"></a>   
## <a name="using-entire-objects-as-a-binding-source"></a>使用整個物件做為繫結來源  
 您可以使用整個物件做為繫結來源。 您可以使用，以指定繫結來源<xref:System.Windows.Data.Binding.Source%2A>或<xref:System.Windows.FrameworkElement.DataContext%2A>屬性，然後提供空白繫結宣告： `{Binding}`。 可以使用這種方法的案例包括繫結到屬於字串型別的物件、繫結到內含您感興趣之多個屬性的物件，或是繫結到集合物件。 如需繫結到整個集合物件的範例，請參閱[使用含階層式資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。  
  
 請注意，您可能必須套用自訂邏輯，如此資料對於繫結目標屬性來說才有意義。 自訂的邏輯可能採用自訂轉換器的形式 （如果預設型別轉換不存在） 或<xref:System.Windows.DataTemplate>。 如需轉換器的詳細資訊，請參閱[資料繫結概觀](data-binding-overview.md)的＜資料轉換＞一節。 如需資料範本的詳細資訊，請參閱[資料範本化概觀](data-templating-overview.md)。  
  
<a name="collections"></a>   
## <a name="using-collection-objects-as-a-binding-source"></a>使用集合物件做為繫結來源  
 您想當做繫結來源的物件通常會是自訂物件的集合。 每個物件都會當做重複繫結的其中一個執行個體的來源。 例如，您可能有一個由 `CustomerOrder` 物件組成的 `CustomerOrders` 集合，而您的應用程式會逐一查看這個集合來判斷訂單數量，以及各筆訂單所包含的資料。  
  
 您可以列舉實作任何集合<xref:System.Collections.IEnumerable>介面。 不過，若要設定動態繫結，以便插入或刪除集合中的更新[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]自動執行，則集合必須實作<xref:System.Collections.Specialized.INotifyCollectionChanged>介面。 這個介面會公開每次基礎集合變更時必須引發的事件。  
  
 <xref:System.Collections.ObjectModel.ObservableCollection%601>類別會公開 （expose） 的資料集合的內建實作<xref:System.Collections.Specialized.INotifyCollectionChanged>介面。 集合中的個別資料物件都必須滿足前幾個章節中描述的需求。 如需範例，請參閱[建立和繫結至 ObservableCollection](how-to-create-and-bind-to-an-observablecollection.md)。 在之前實作您自己的集合，請考慮使用<xref:System.Collections.ObjectModel.ObservableCollection%601>或其中一個現有的集合類別，例如<xref:System.Collections.Generic.List%601>， <xref:System.Collections.ObjectModel.Collection%601>，和<xref:System.ComponentModel.BindingList%601>，還有其他更多。  
  
 WPF 絕不會直接繫結至集合。 如果您指定集合做為繫結來源，WPF 實際上會繫結至集合的預設檢視。 如需預設檢視的詳細資訊，請參閱[資料繫結概觀](data-binding-overview.md)。  
  
 如果您擁有進階的案例，而且您想要實作您自己的集合，請考慮使用<xref:System.Collections.IList>介面。 <xref:System.Collections.IList> 提供非泛型集合之物件的可個別存取的索引，以改善效能。  
  
<a name="permissions"></a>   
## <a name="permission-requirements-in-data-binding"></a>資料繫結的使用權限需求  
 進行資料繫結時，您必須考慮應用程式的信任層級。 下表摘要說明在以完全信任或部分信任執行的應用程式中，可以當做繫結目標的屬性型別：  
  
|屬性類型<br /><br /> (所有存取修飾詞)|動態物件屬性|動態物件屬性|CLR 屬性|CLR 屬性|相依性屬性|相依性屬性|  
|------------------------------------------------|-----------------------------|-----------------------------|------------------|------------------|-------------------------|-------------------------|  
|**信任層級**|**完全信任**|**部分信任**|**完全信任**|**部分信任**|**完全信任**|**部分信任**|  
|公用類別|是|是|是|是|是|是|  
|非公用類別|是|否|[是]|否|是|是|  
  
 這個表格說明資料繫結中使用權限需求的下列相關重點：  
  
- 對於 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性，只要繫結引擎能夠使用反映來存取繫結來源屬性，資料繫結就有作用。 否則，繫結引擎將會發出找不到屬性的警告，並使用後援值或預設值 (如果有的話)。  
  
- 您可以繫結至在編譯階段或執行階段定義之動態物件上的屬性。  
  
- 您永遠都可以繫結至相依性屬性。  
  
 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 繫結也有類似的使用權限需求。 在部分信任沙箱，<xref:System.Windows.Data.XmlDataProvider>它並沒有指定的資料存取權限時失敗。  
  
 具有匿名型別的物件為內部物件。 只有在完全信任狀況下執行時，您才能繫結至匿名型別的屬性。 如需匿名型別的詳細資訊，請參閱[匿名型別 (C# 程式設計手冊)](~/docs/csharp/programming-guide/classes-and-structs/anonymous-types.md) 或[匿名型別 (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) (Visual Basic)。  
  
 如需部分信任安全性的詳細資訊，請參閱 [WPF 部分信任安全性](../wpf-partial-trust-security.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.ObjectDataProvider>
- <xref:System.Windows.Data.XmlDataProvider>
- [指定繫結來源](how-to-specify-the-binding-source.md)
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
- [WPF 資料繫結與 LINQ to XML 概觀](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [資料繫結](../advanced/optimizing-performance-data-binding.md)
